---
toc: true
layout: post
description: 
categories: [backend]
title: Spring Boot
comments: true
---

# JPA

JPA (Java Persistence API) allows access to data between Java objects. JPA includes many types of implementations, the most popular being Hibernate, which allows abstraction for object relational mapping (ORM). ORM allows a Java class to be mapped to a database. 

The architecture of JPA includes several features such as `Entity`, which persistence objects within the database. 

## Repository

Spring Data JPA provides abstraction for Hibernate. It provides simplification by using the repository to access databases, which removes the need to use SQL. 

A repository must extend from one of the three following repositories: `JPARepository`, `PagingAndSortingRepository`, or `CrudRepository`. Most of the time, it is extended to `JPARepository`

In the repository file, th interface is written as: <code>public interface <em>repository name</em> extends JpaRepository<></code>. The question is, what does `<>` mean? 

In `<>`, there are two generics that need to be configured. The first is the entity, and the second is the data type for the id. 

# How to create a Spring Boot JPA (In Progress)

First, create a file titled <code><em>name</em>.java</code>. Within the file, mark the class as an Entity with `@Entity`, and mark the id with `@Id`. In addition, create getters and setters for each variable. 

## Controller

Create a file titled <code><em>name</em>Controller.java</code>. Use `@RestController` to mark the class as a controller
