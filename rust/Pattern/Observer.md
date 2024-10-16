# Observer Pattern
It is widely used to enable objects to observe changes in other objects.

The observer pattern provides looser coupling, makes it easier to attach and
detach observers (equivalent callbacks), and enables us to have a 
**many-to-one** relationship instead of one-to-one.

Advantage: we can use the observer pattern when we have code that needs to 
notify other code about events (the subject) without needing a dependency on 
the observers.
```
+-------------------+
|   trait           |
|   Subject         |
+-------------------+
| +attach(Observer) |
| +detach(Observer) |
| +update()         |
+-------------------+
        |
        |
        v
+-------------------+
|   trait           |
|   Observer        |
+-------------------+
| +observe(Subject) |
+-------------------+
```

# Code
```rust
use std::sync::Arc;
use std::sync::Weak;

// for objects that want to observe others
pub trait Observer {
    type Subject;
    fn observe(&self, subject: &Self::Subject);
}

// implemented by objects that want to allow other objects to observe them
pub trait Observable {
    type Observer;
    fn update(&self);
    fn attach(&mut self, observer: Self::Observer);
    fn detach(&mut self, observer: Self::Observer);
}

pub struct Subject {
    observers: Vec<Weak<dyn Observer<Subject = Self>>>,
    state: String,
}

impl Observable for Subject {
    type Observer = Arc<dyn Observer<Subject = Self>>;
    fn update(&self) {
        self.observers
            .iter()
            .flat_map(|o| o.upgrade())
            .for_each(|o| o.observe(self));
    }
    fn attach(&mut self, observer: Self::Observer) {
        self.observers.push(Arc::downgrade(&observer));
    }
    fn detach(&mut self, observer: Self::Observer) {
        self.observers
            .retain(|f| {
                !f.ptr_eq(&Arc::downgrade(&observer))
            });
    }
}

impl Subject {
    pub fn new(state: &str) -> Self {
        Self {
            observers: vec![],
            state: state.into(),
        }
    }

    pub fn state(&self) -> &str {
        self.state.as_ref()
    }
}

struct MyObserver {
    name: String,
}

impl MyObserver {
    fn new(name: &str) -> Arc<Self> {
        Arc::new(Self { name: name.into() })
    }
}

impl Observer for MyObserver {
    type Subject = Subject;
    fn observe(&self, subject: &Self::Subject) {
        println!(
            "observed subject with state={:?} in {}",
            subject.state(),
            self.name
        );
    }
}

fn main() {
    let mut subject = Subject::new("some subject state");

    let observer1 = MyObserver::new("observer1");
    let observer2 = MyObserver::new("observer2");

    subject.attach(observer1.clone());
    subject.attach(observer2.clone());

    subject.update();
}
```
