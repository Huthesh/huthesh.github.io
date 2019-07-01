---
title: Spring beans with XML configuration
layout: default
description: huthesh.github.io
categories: [Spring]
---
<ol class="breadcrumb">
  <li><a href="/Spring">Spring</a></li>
  <li class="active">Spring beans with XML configuration</li>
</ol>

<div>
        {{ page.date | date: "%-d %B %Y" }}
</div>

## Spring beans with XML configuration

### Create a Model class

<div>
<pre class="prettyprint">
<code class="prettyprint language-java">
package io.github.huthesh.model;
public class Customer {
	private String firstName;
	private String lastName;
	public String getFirstName() {
		return firstName;
	}
	public String getLastName() {
		return lastName;
	}
	public void setFirstName(String firstName) {
		this.firstName = firstName;
	}
	public void setLastName(String lastName) {
		this.lastName = lastName;
	}
	@Override
	public String toString() {
		return "Customer [firstName=" + firstName + ", lastName=" + lastName + "]";
	}
}
</code>
</pre>
</div>

### Create a Repository Interface and its implementation

<div>
<pre class="prettyprint">
<code class="prettyprint language-java">
package io.github.huthesh.repository;
import java.util.List;
import io.github.huthesh.model.Customer;
public interface CustomerRepository {
	public List &lt;Customer&gt; findAll();
}
</code>
</pre>
</div>


<div>
<pre class="prettyprint">
<code class="prettyprint language-java">
package io.github.huthesh.repository;
import java.util.Arrays;
import java.util.List;
import io.github.huthesh.model.Customer;
public class InMemoryDbReposistoryImpl implements CustomerRepository {
	@Override
	public List &lt;Customer&gt; findAll() {
		Customer customer=new Customer();
		customer.setFirstName("Huthesh");
		customer.setLastName("Karkada");
		return Arrays.asList(customer);
	}
}
</code>
</pre>
</div>

### Create service interface and Implementation

<div>
<pre class="prettyprint">
<code class="prettyprint language-java">
package io.github.huthesh.service;
import java.util.List;
import io.github.huthesh.model.Customer;
public interface CustomerService {
	public List&lt;Customer&gt; findAll();
}
</code>
</pre>
</div>

<div>
<pre class="prettyprint">
<code class="prettyprint language-java">
package io.github.huthesh.service;
import java.util.List;
import io.github.huthesh.model.Customer;
import io.github.huthesh.repository.CustomerRepository;
public class CustomerServiceImpl implements CustomerService {
	CustomerRepository customerRepository;
	@Override
	public List&lt;Customer&gt; findAll() {
		return this.customerRepository.findAll();
	}
	/*Setter method is used for setter injection*/
	public void setCustomerRepository(CustomerRepository customerRepository) {
		this.customerRepository = customerRepository;
	}
}
</code>
</pre>
</div>
