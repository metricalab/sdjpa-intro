# Spring Data JPA - Introduction to Spring Data JPA

This repository contains source code examples to support my course Spring Data JPA and Hibernate Beginner to Guru

You can access the API documentation [here](https://sfg-beer-works.github.io/brewery-api/#tag/Beer-Service)

## Connect with Spring Framework Guru
* Spring Framework Guru [Blog](https://springframework.guru/)
* Subscribe to Spring Framework Guru on [YouTube](https://www.youtube.com/channel/UCrXb8NaMPQCQkT8yMP_hSkw)
* Like Spring Framework Guru on [Facebook](https://www.facebook.com/springframeworkguru/)
* Follow Spring Framework Guru on [Twitter](https://twitter.com/spring_guru)
* Connect with John Thompson on [LinkedIn](http://www.linkedin.com/in/springguru)

# sdjpa-intro branch -> liq-add-table

- 1 Launch in your sql editor workbench this script (root account):

```
drop table if exists book;
drop table if exists hibernate_sequence;

create table book (
                      id bigint not null,
                      isbn varchar(255),
                      publisher varchar(255),
                      title varchar(255),
                      primary key (id)
) engine=InnoDB;

create table hibernate_sequence (
    next_val bigint
) engine=InnoDB;

insert into hibernate_sequence values ( 1 );
```

- 2 From a terminal in the base folder of the project launch:

```
./mvnw spring-boot:run
```

- 3 Generate a change log base

If you need to add liquibase to a project first step is generate a log base. In that case you could generate this file launching the next command:

```
mvn liquibase:generateChangeLog
```

This command generates a file called **changelog.xml** with the schema of the database. This file will be the baseline
(baseline-changelog.xml) to start your liquid-base project. In our example we have 4 files:

- changelog-master: main file that address the other 3 files. Inside the file the order of the files are important. This file allows to check the history of all the updates in our database:

    - 1 - baseline-changelog.xml
    - 2 - init-hibernate.xml
    - 3 - add-author.xml

