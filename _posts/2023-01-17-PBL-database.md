---
keywords: fastai
title: Database/Model, Backend, OOP, Python
badges: false
toc: true
categories: [week19]
nb_path: _notebooks/2023-01-17-PBL-database.ipynb
layout: notebook
---

<!--
#################################################
### THIS FILE WAS AUTOGENERATED! DO NOT EDIT! ###
#################################################
# file to edit: _notebooks/2023-01-17-PBL-database.ipynb
-->

<div class="container" id="notebook-container">
        
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Database-and-Table-Terms">Database and Table Terms<a class="anchor-link" href="#Database-and-Table-Terms"> </a></h2><blockquote><p>The foundations of database is defining one or more <strong><em>Tables</em></strong>.  In Python, a database can be constructed using the foundations we learned in modeling a Class.</p>
<ul>
<li>A "Table" is a Model/Schema within a Database.  </li>
<li>A "Table" definition in Python/SQLAlchemy is manifested by defining a "<strong><em>Class</em></strong>" and "<strong><em>Attributes</em></strong>" in Python.  </li>
<li>A Python <strong><em>Class can inherit database functionality</em></strong> from SQLAlchemy.  This is a method Python developers use to turn a Class into a Table within a <strong><em>SQL Database</em></strong>.</li>
<li>Writing methods in the Class for Create, Read, Update, Delete (<strong><em>CRUD</em></strong>) is how a developer initiates database operations.</li>
</ul>
</blockquote>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Reference">Reference<a class="anchor-link" href="#Reference"> </a></h3><ul>
<li><a href="https://www.sqlalchemy.org/">SQLAlchemy</a></li>
<li><a href="https://www.ffnext.io/blog/python-backend-with-flask-for-beginners#:~:text=You%20can%20create%20an%20HTTP,command%3A%20python%20app.py.">Python Backend with Flask, SQLite</a></li>
<li><a href="https://www.ffnext.io/blog/python-backend-with-flask-for-beginners#:~:text=You%20can%20create%20an%20HTTP,command%3A%20python%20app.py.">Python Backend starting Controller</a></li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Outline-for-Backend-Model-and-Database">Outline for Backend Model and Database<a class="anchor-link" href="#Outline-for-Backend-Model-and-Database"> </a></h3><blockquote><p><strong><em>OOP modeling with SQLAlchemy</em></strong> enables CRUD operations.</p>
</blockquote>
<ol>
<li><a href="https://github.com/nighthawkcoders/flask_portfolio/blob/main/model/users.py#L72-L80">Users Table Schema</a></li>
<li><p><a href="https://github.com/nighthawkcoders/flask_portfolio/blob/main/model/users.py#L72-L80">Database Properties</a></p>
</li>
<li><p><a href="https://github.com/nighthawkcoders/flask_portfolio/blob/main/main.py#L38-L41">Initial Database Setup (call)</a></p>
</li>
<li><p><a href="https://github.com/nighthawkcoders/flask_portfolio/blob/main/main.py#L38-L41">Initial Database Setup (add records)</a></p>
</li>
<li><p><a href="https://github.com/nighthawkcoders/flask_portfolio/blob/main/model/users.py#L72-L80">OOP CRUD operations</a></p>
</li>
</ol>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="User-Table-Schema">User Table Schema<a class="anchor-link" href="#User-Table-Schema"> </a></h4><blockquote><p>The db.Model is inherited into the <code>class User(db.model)</code>, Each <code>db.Column</code> is provided properties according to capabilities of SQL.  See <strong>init</strong>.py for db object definition.</p>
</blockquote>
<div class="highlight"><pre><span></span><span class="n">db</span> <span class="o">=</span> <span class="n">SQLAlchemy</span><span class="p">(</span><span class="n">app</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>
    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="sd">&quot;&quot;&quot; database dependencies to support sqliteDB examples &quot;&quot;&quot;</span>

<span class="kn">from</span> <span class="nn">__init__</span> <span class="kn">import</span> <span class="n">app</span><span class="p">,</span> <span class="n">db</span>
<span class="kn">from</span> <span class="nn">sqlalchemy.exc</span> <span class="kn">import</span> <span class="n">IntegrityError</span>
<span class="kn">from</span> <span class="nn">werkzeug.security</span> <span class="kn">import</span> <span class="n">generate_password_hash</span><span class="p">,</span> <span class="n">check_password_hash</span>


<span class="sd">&quot;&quot;&quot; Key additions to User Class for Schema definition &quot;&quot;&quot;</span>

<span class="c1"># Define the User class to manage actions in the &#39;users&#39; table</span>
<span class="c1"># -- Object Relational Mapping (ORM) is the key concept of SQLAlchemy</span>
<span class="c1"># -- a.) db.Model is like an inner layer of the onion in ORM</span>
<span class="c1"># -- b.) User represents data we want to store, something that is built on db.Model</span>
<span class="c1"># -- c.) SQLAlchemy ORM is layer on top of SQLAlchemy Core, then SQLAlchemy engine, SQL</span>
<span class="k">class</span> <span class="nc">User</span><span class="p">(</span><span class="n">db</span><span class="o">.</span><span class="n">Model</span><span class="p">):</span>
    <span class="n">__tablename__</span> <span class="o">=</span> <span class="s1">&#39;users&#39;</span>  <span class="c1"># table name is plural, class name is singular</span>

    <span class="c1"># Define the User schema with &quot;vars&quot; from object</span>
    <span class="nb">id</span> <span class="o">=</span> <span class="n">db</span><span class="o">.</span><span class="n">Column</span><span class="p">(</span><span class="n">db</span><span class="o">.</span><span class="n">Integer</span><span class="p">,</span> <span class="n">primary_key</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
    <span class="n">_name</span> <span class="o">=</span> <span class="n">db</span><span class="o">.</span><span class="n">Column</span><span class="p">(</span><span class="n">db</span><span class="o">.</span><span class="n">String</span><span class="p">(</span><span class="mi">255</span><span class="p">),</span> <span class="n">unique</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">nullable</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
    <span class="n">_uid</span> <span class="o">=</span> <span class="n">db</span><span class="o">.</span><span class="n">Column</span><span class="p">(</span><span class="n">db</span><span class="o">.</span><span class="n">String</span><span class="p">(</span><span class="mi">255</span><span class="p">),</span> <span class="n">unique</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">nullable</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
    <span class="n">_password</span> <span class="o">=</span> <span class="n">db</span><span class="o">.</span><span class="n">Column</span><span class="p">(</span><span class="n">db</span><span class="o">.</span><span class="n">String</span><span class="p">(</span><span class="mi">255</span><span class="p">),</span> <span class="n">unique</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">nullable</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
    <span class="n">_dob</span> <span class="o">=</span> <span class="n">db</span><span class="o">.</span><span class="n">Column</span><span class="p">(</span><span class="n">db</span><span class="o">.</span><span class="n">Date</span><span class="p">)</span>

    <span class="c1"># Defines a relationship between User record and Notes table, one-to-many (one user to many notes)</span>
    <span class="n">posts</span> <span class="o">=</span> <span class="n">db</span><span class="o">.</span><span class="n">relationship</span><span class="p">(</span><span class="s2">&quot;Post&quot;</span><span class="p">,</span> <span class="n">cascade</span><span class="o">=</span><span class="s1">&#39;all, delete&#39;</span><span class="p">,</span> <span class="n">backref</span><span class="o">=</span><span class="s1">&#39;users&#39;</span><span class="p">,</span> <span class="n">lazy</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>

    <span class="c1"># constructor of a User object, initializes the instance variables within object (self)</span>
    <span class="k">def</span> <span class="fm">__init__</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="n">noc</span><span class="p">,</span> <span class="n">date</span><span class="o">=</span><span class="n">date</span><span class="o">.</span><span class="n">today</span><span class="p">(),</span> <span class="n">homeworkName</span><span class="p">):</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">_noc</span> <span class="o">=</span> <span class="n">noc</span>    <span class="c1"># variables with self prefix become part of the object, </span>
        <span class="bp">self</span><span class="o">.</span><span class="n">_homeworkName</span> <span class="o">=</span> <span class="n">homeworkName</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">_date</span> <span class="o">=</span> <span class="n">date</span>
</pre></div>

    </div>
</div>
</div>

</div>
    {% endraw %}

    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="k">def</span> <span class="nf">create</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span>
    <span class="k">try</span><span class="p">:</span>
        <span class="c1"># creates a person object from User(db.Model) class, passes initializers</span>
        <span class="n">db</span><span class="o">.</span><span class="n">session</span><span class="o">.</span><span class="n">add</span><span class="p">(</span><span class="bp">self</span><span class="p">)</span>  <span class="c1"># add prepares to persist person object to Users table</span>
        <span class="n">db</span><span class="o">.</span><span class="n">session</span><span class="o">.</span><span class="n">commit</span><span class="p">()</span>  <span class="c1"># SqlAlchemy &quot;unit of work pattern&quot; requires a manual commit</span>
        <span class="k">return</span> <span class="bp">self</span>
    <span class="k">except</span> <span class="n">IntegrityError</span><span class="p">:</span>
        <span class="n">db</span><span class="o">.</span><span class="n">session</span><span class="o">.</span><span class="n">remove</span><span class="p">()</span>
        <span class="k">return</span> <span class="kc">None</span>

<span class="c1"># CRUD read converts self to dictionary</span>
<span class="c1"># returns dictionary</span>
<span class="k">def</span> <span class="nf">read</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span>
    <span class="k">return</span> <span class="p">{</span>
        <span class="s2">&quot;id&quot;</span><span class="p">:</span> <span class="bp">self</span><span class="o">.</span><span class="n">id</span><span class="p">,</span>
        <span class="s2">&quot;name&quot;</span><span class="p">:</span> <span class="bp">self</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
        <span class="s2">&quot;uid&quot;</span><span class="p">:</span> <span class="bp">self</span><span class="o">.</span><span class="n">uid</span><span class="p">,</span>
        <span class="s2">&quot;dob&quot;</span><span class="p">:</span> <span class="bp">self</span><span class="o">.</span><span class="n">dob</span><span class="p">,</span>
        <span class="s2">&quot;age&quot;</span><span class="p">:</span> <span class="bp">self</span><span class="o">.</span><span class="n">age</span><span class="p">,</span>
        <span class="s2">&quot;posts&quot;</span><span class="p">:</span> <span class="p">[</span><span class="n">post</span><span class="o">.</span><span class="n">read</span><span class="p">()</span> <span class="k">for</span> <span class="n">post</span> <span class="ow">in</span> <span class="bp">self</span><span class="o">.</span><span class="n">posts</span><span class="p">]</span>
    <span class="p">}</span>

<span class="c1"># CRUD update: updates user name, password, phone</span>
<span class="c1"># returns self</span>
<span class="k">def</span> <span class="nf">update</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="n">name</span><span class="o">=</span><span class="s2">&quot;&quot;</span><span class="p">,</span> <span class="n">uid</span><span class="o">=</span><span class="s2">&quot;&quot;</span><span class="p">,</span> <span class="n">password</span><span class="o">=</span><span class="s2">&quot;&quot;</span><span class="p">):</span>
    <span class="sd">&quot;&quot;&quot;only updates values with length&quot;&quot;&quot;</span>
    <span class="k">if</span> <span class="nb">len</span><span class="p">(</span><span class="n">name</span><span class="p">)</span> <span class="o">&gt;</span> <span class="mi">0</span><span class="p">:</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">name</span> <span class="o">=</span> <span class="n">name</span>
    <span class="k">if</span> <span class="nb">len</span><span class="p">(</span><span class="n">uid</span><span class="p">)</span> <span class="o">&gt;</span> <span class="mi">0</span><span class="p">:</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">uid</span> <span class="o">=</span> <span class="n">uid</span>
    <span class="k">if</span> <span class="nb">len</span><span class="p">(</span><span class="n">password</span><span class="p">)</span> <span class="o">&gt;</span> <span class="mi">0</span><span class="p">:</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">set_password</span><span class="p">(</span><span class="n">password</span><span class="p">)</span>
    <span class="n">db</span><span class="o">.</span><span class="n">session</span><span class="o">.</span><span class="n">commit</span><span class="p">()</span>
    <span class="k">return</span> <span class="bp">self</span>

<span class="c1"># CRUD delete: remove self</span>
<span class="c1"># None</span>
<span class="k">def</span> <span class="nf">delete</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span>
    <span class="n">db</span><span class="o">.</span><span class="n">session</span><span class="o">.</span><span class="n">delete</span><span class="p">(</span><span class="bp">self</span><span class="p">)</span>
    <span class="n">db</span><span class="o">.</span><span class="n">session</span><span class="o">.</span><span class="n">commit</span><span class="p">()</span>
    <span class="k">return</span> <span class="kc">None</span>
</pre></div>

    </div>
</div>
</div>

</div>
    {% endraw %}

    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="k">if</span> <span class="vm">__name__</span> <span class="o">==</span> <span class="s2">&quot;__main__&quot;</span><span class="p">:</span>
    <span class="n">u1</span> <span class="o">=</span> <span class="n">User</span><span class="p">(</span><span class="n">name</span><span class="o">=</span><span class="s1">&#39;Sean Y&#39;</span><span class="p">,</span> <span class="n">uid</span><span class="o">=</span><span class="s1">&#39;yeung&#39;</span><span class="p">,</span> <span class="n">password</span><span class="o">=</span><span class="s1">&#39;123yeung&#39;</span><span class="p">,</span> <span class="n">dob</span><span class="o">=</span><span class="n">date</span><span class="p">(</span><span class="mi">1995</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">),</span> <span class="n">height</span><span class="o">=</span><span class="s1">&#39;10 feet&#39;</span><span class="p">)</span>
    <span class="n">u2</span> <span class="o">=</span> <span class="n">User</span><span class="p">(</span><span class="n">name</span><span class="o">=</span><span class="s1">&#39;Ellie P&#39;</span><span class="p">,</span> <span class="n">uid</span><span class="o">=</span><span class="s1">&#39;ellie&#39;</span><span class="p">,</span> <span class="n">password</span><span class="o">=</span><span class="s1">&#39;123ellie&#39;</span><span class="p">,</span> <span class="n">dob</span><span class="o">=</span><span class="n">date</span><span class="p">(</span><span class="mi">2007</span><span class="p">,</span> <span class="mi">11</span><span class="p">,</span> <span class="mi">1</span><span class="p">),</span> <span class="n">height</span><span class="o">=</span><span class="s1">&#39;10 feet&#39;</span><span class="p">)</span>
    <span class="n">u3</span> <span class="o">=</span> <span class="n">User</span><span class="p">(</span><span class="n">name</span><span class="o">=</span><span class="s1">&#39;Kaylee H&#39;</span><span class="p">,</span> <span class="n">uid</span><span class="o">=</span><span class="s1">&#39;kaylee&#39;</span><span class="p">,</span> <span class="n">password</span><span class="o">=</span><span class="s1">&#39;123kaylee&#39;</span><span class="p">,</span> <span class="n">dob</span><span class="o">=</span><span class="n">date</span><span class="p">(</span><span class="mi">2005</span><span class="p">,</span> <span class="mi">10</span><span class="p">,</span> <span class="mi">30</span><span class="p">),</span> <span class="n">height</span><span class="o">=</span><span class="s1">&#39;10 feet&#39;</span><span class="p">)</span>
    <span class="n">u4</span> <span class="o">=</span> <span class="n">User</span><span class="p">(</span><span class="n">name</span><span class="o">=</span><span class="s1">&#39;Theo H&#39;</span><span class="p">,</span> <span class="n">uid</span><span class="o">=</span><span class="s1">&#39;theo&#39;</span><span class="p">,</span> <span class="n">password</span><span class="o">=</span><span class="s1">&#39;123theo&#39;</span><span class="p">,</span> <span class="n">dob</span><span class="o">=</span><span class="n">date</span><span class="p">(</span><span class="mi">2006</span><span class="p">,</span> <span class="mi">1</span><span class="p">,</span> <span class="mi">31</span><span class="p">),</span> <span class="n">height</span><span class="o">=</span><span class="s1">&#39;10 feet&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
    {% endraw %}

    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="kn">from</span> <span class="nn">flask</span> <span class="kn">import</span> <span class="n">Flask</span>
<span class="kn">from</span> <span class="nn">flask_login</span> <span class="kn">import</span> <span class="n">LoginManager</span>
<span class="kn">from</span> <span class="nn">flask_sqlalchemy</span> <span class="kn">import</span> <span class="n">SQLAlchemy</span>
<span class="kn">from</span> <span class="nn">flask_migrate</span> <span class="kn">import</span> <span class="n">Migrate</span>

<span class="sd">&quot;&quot;&quot;</span>
<span class="sd">These object can be used throughout project.</span>
<span class="sd">1.) Objects from this file can be included in many blueprints</span>
<span class="sd">2.) Isolating these object definitions avoids duplication and circular dependencies</span>
<span class="sd">&quot;&quot;&quot;</span>

<span class="c1"># Setup of key Flask object (app)</span>
<span class="n">app</span> <span class="o">=</span> <span class="n">Flask</span><span class="p">(</span><span class="vm">__name__</span><span class="p">)</span>
<span class="c1"># Setup SQLAlchemy object and properties for the database (db)</span>
<span class="n">dbURI</span> <span class="o">=</span> <span class="s1">&#39;sqlite:////volumes/flask_portfolio.db&#39;</span>
<span class="n">app</span><span class="o">.</span><span class="n">config</span><span class="p">[</span><span class="s1">&#39;SQLALCHEMY_TRACK_MODIFICATIONS&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="kc">False</span>
<span class="n">app</span><span class="o">.</span><span class="n">config</span><span class="p">[</span><span class="s1">&#39;SQLALCHEMY_DATABASE_URI&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">dbURI</span>
<span class="n">app</span><span class="o">.</span><span class="n">config</span><span class="p">[</span><span class="s1">&#39;SECRET_KEY&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="s1">&#39;SECRET_KEY&#39;</span>
<span class="n">db</span> <span class="o">=</span> <span class="n">SQLAlchemy</span><span class="p">(</span><span class="n">app</span><span class="p">)</span>
<span class="n">Migrate</span><span class="p">(</span><span class="n">app</span><span class="p">,</span> <span class="n">db</span><span class="p">)</span>

<span class="c1"># Images storage</span>
<span class="n">app</span><span class="o">.</span><span class="n">config</span><span class="p">[</span><span class="s1">&#39;MAX_CONTENT_LENGTH&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="mi">5</span> <span class="o">*</span> <span class="mi">1024</span> <span class="o">*</span> <span class="mi">1024</span>  <span class="c1"># maximum size of uploaded content</span>
<span class="n">app</span><span class="o">.</span><span class="n">config</span><span class="p">[</span><span class="s1">&#39;UPLOAD_EXTENSIONS&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;.jpg&#39;</span><span class="p">,</span> <span class="s1">&#39;.png&#39;</span><span class="p">,</span> <span class="s1">&#39;.gif&#39;</span><span class="p">]</span>  <span class="c1"># supported file types</span>
<span class="n">app</span><span class="o">.</span><span class="n">config</span><span class="p">[</span><span class="s1">&#39;UPLOAD_FOLDER&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="s1">&#39;volumes/uploads/&#39;</span>  <span class="c1"># location of user uploaded content</span>
</pre></div>

    </div>
</div>
</div>

</div>
    {% endraw %}

<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Hacks">Hacks<a class="anchor-link" href="#Hacks"> </a></h2><blockquote><p>The <strong><em>Big Picture</em></strong> purpose of this hack is to build a database.  Being able to create an SQLite table and populate test data within it is the major goal.  To do this effectively it is imperative to show the following.</p>
<ol>
<li>Build Schema for a table, make a new <code>model</code> file and use <code>users.py</code> as an example. Start slow and simple and build up.</li>
<li>Build an <code>initXXXXX()</code> method and use it to add preliminary/test data to the table.  Once again use users.py as an example.</li>
<li>Make a 30-60 second video where you show a Debugging session of making new rows in the table. Use <code>sqlite</code> marketplace tools and/or sqlite3 command line tool to show success in creating table and adding data.</li>
</ol>
</blockquote>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Hack-Helper">Hack Helper<a class="anchor-link" href="#Hack-Helper"> </a></h2><blockquote><p>Here are some tips.</p>
</blockquote>
<ul>
<li><p>Become familiar with <code>initUsers()</code>.  Observe it is called/activated from <code>main.py</code>.  This function activates after you run the <code>main.py</code> and activate the web application in the browser.  Observe that the <code>sqlite.db</code> file will appear in the volumes directory in conjunction with home screen of site appearing in browser.</p>
</li>
<li><p>Delete sqlite.db from volumes directory on your development machine.  Set <code>breakpoint</code> on initUsers() and run <code>main.py using debug</code>.  Use the step into option on the debugger and observe the creation of data.</p>
</li>
</ul>
<div class="highlight"><pre><span></span><span class="nd">@app</span><span class="o">.</span><span class="n">before_first_request</span>
<span class="k">def</span> <span class="nf">activate_job</span><span class="p">():</span><span class="n">initJokes</span><span class="p">()</span>    <span class="n">initUsers</span><span class="p">()</span>
</pre></div>
<ul>
<li><p>Make your own <code>XXXXX.py</code> file under <code>model</code> directory.  Follow <code>users.py</code> and develop your own schema from the OOP code you did in last Hacks.  Follow the pattern in <code>users.py</code> to make a initXXXX() function top populate some test data.</p>
</li>
<li><p>In <code>main.py</code>, add your initXXXX() method to <code>def activate_job()</code> function shown above.  Use this as basis of your video debugging session.  Debugging is hugely important at this level to understand your database success prior to building an API.  Building initXXXX() method, adding database records, and debugging will enable you to verify CRUD operations as you develop.</p>
</li>
</ul>

</div>
</div>
</div>
</div>
 

