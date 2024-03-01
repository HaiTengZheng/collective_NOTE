# more security
> sudo mysql_secure_installation

# create database
> CREATE DATABASE database_name;

## 告诉 mysql 本库的表默认使用的字符是拉丁文及其他字符
> CHARACTER SET latin1

## 告诉 mysql 数据的存储方式是二进制拉丁字符
> COLLATE latin1_bin

# 看表建成
> DESCRIPE table_name;

# access mysql through command line
