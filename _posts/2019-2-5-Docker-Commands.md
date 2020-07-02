---
title: Docker commands
layout: default
description: huthesh.github.io
categories: [Docker]
---
<div class="container margintop">
<ol class="breadcrumb">
  <li><a href="/Docker">Docker</a></li>
  <li class="active">Docker commands</li>
</ol>

<div>
        {{ page.date | date: "%-d %B %Y" }}
</div>
<br>
<br>
<h3>Installing docker on linux</h3>
<pre>
curl -fsSL https://test.docker.com -o test-docker.sh
</pre>
<br>
<h3>Controlling docker daemon</h3>
<pre>
systemctl start|stop|restart|status docker
</pre>
<br>
<h3>Docker engine components</h3>
<img src="/assets/images/dockerd.png" alt="" style="width:500px;height:500px;">
</div>