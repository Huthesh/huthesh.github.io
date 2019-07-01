---
title: Type of dependency injection
layout: default
description: huthesh.github.io
categories: [Spring]
---
<ol class="breadcrumb">
  <li><a href="/Spring">Spring</a></li>
  <li class="active"> Type of dependency injection</li>
</ol>

<div>
        {{ page.date | date: "%-d %B %Y" }}
</div>

## Types of dependency injection

<b>1  Setter injection</b>

Implementation class should have setter method for the bean to be injected

```java
package io.github.huthesh.service;

import java.util.List;

import io.github.huthesh.model.Customer;
import io.github.huthesh.repository.CustomerRepository;

public class CustomerServiceImpl implements CustomerService {

	CustomerRepository customerRepository;
	
	@Override
	public List<Customer> findAll() {
		return this.customerRepository.findAll();
	}

	/*Setter for injecting the Dependency*/
	public void setCustomerRepository(CustomerRepository customerRepository) {
		this.customerRepository = customerRepository;
	}

}
```

XML config should have bean property set as follows. Here Spring will inject "customerRepositoryBean" to "customerRepository"  in "CustomerServiceImpl" through setter
```xml
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="
http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-3.0.xsd">

	<bean name="customerRepositoryBean"
		class="io.github.huthesh.repository.InMemoryDbReposistoryImpl" />
		
	<bean name="customerServiceImplBean"
		class="io.github.huthesh.service.CustomerServiceImpl">
		<property name="customerRepository" ref="customerRepositoryBean"></property>	
	</bean>

</beans>
```
<b>2  Constructor injection</b>

Implementation class should have a non default constructor for the bean to be injected

```java
package io.github.huthesh.service;

import java.util.List;

import io.github.huthesh.model.Customer;
import io.github.huthesh.repository.CustomerRepository;

public class CustomerServiceImpl implements CustomerService {

	CustomerRepository customerRepository=null;
	
	@Override
	public List<Customer> findAll() {
		return this.customerRepository.findAll();
	}

	/*Constructor for injecting the Dependency*/
	public CustomerServiceImpl(CustomerRepository customerRepository) {
		super();
		this.customerRepository = customerRepository;
	}


}

```

XML config should have bean property set as follows. Here Spring will inject "customerRepositoryBean" to "customerRepository"  in "CustomerServiceImpl" through Constructor
```xml
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="
http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-3.0.xsd">

	<bean name="customerRepositoryBean"
		class="io.github.huthesh.repository.InMemoryDbReposistoryImpl" />
		
	<bean name="customerServiceImplBean"
		class="io.github.huthesh.service.CustomerServiceImpl">	
		<constructor-arg index="0" name="customerRepository" ref="customerRepositoryBean"/>	
	</bean>

</beans>
```

<b>3  Autowire</b>

Autowire has three types
- no -- By default. No autowiring
-  "byName"  ---- Autowiring by property name. If a bean of class Cat exposes a "dog" property, Spring will try to set this to the value of the bean "dog" in the current container. If there is no matching bean by name, nothing special happens.
- "byType" ---- Autowiring if there is exactly one bean of the property type in the container. If there is more than one, a fatal error is raised, and you cannot use byType autowiring for that bean. If there is none, nothing special happens. 
- "constructor" ---- Analogous to "byType" for constructor arguments. If there is not exactly one bean of the constructor argument type in the bean factory, a fatal error 

Autowiring type is specified in the XML file as shown below. "autowire" attribute in the "bean" tag will have specific autowiring type

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="
http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-3.0.xsd">

	<bean name="customerRepository"
		class="io.github.huthesh.repository.InMemoryDbReposistoryImpl" />
		
	<bean name="customerServiceImplBean"
		class="io.github.huthesh.service.CustomerServiceImpl" autowire="constructor">
		
	</bean>

</beans>
```

<b>4  Run application</b>

Following is an example of running standalone Spring application

```java
import org.springframework.context.support.ClassPathXmlApplicationContext;

import io.github.huthesh.service.CustomerService;

public class Application {
	public static void main(String[] args) {
		ClassPathXmlApplicationContext applicationContext=new ClassPathXmlApplicationContext("applicationcontext.xml");
		CustomerService bean = applicationContext.getBean("customerServiceImplBean",io.github.huthesh.service.CustomerService.class);
		System.out.println(bean.findAll());
		applicationContext.close();
	}
}
```