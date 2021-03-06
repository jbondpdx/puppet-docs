---
layout: default
built_from_commit: 46e5188e3d20d712525caf5566fa2214e524637d
title: 'Man Page: puppet config'
canonical: "/puppet/latest/man/config.html"
---

<div class='mp'>
<h2 id="NAME">NAME</h2>
<p class="man-name">
  <code>puppet-config</code> - <span class="man-whatis">Interact with Puppet's settings.</span>
</p>

<h2 id="SYNOPSIS">SYNOPSIS</h2>

<p>puppet config <var>action</var> [--section SECTION_NAME]</p>

<h2 id="DESCRIPTION">DESCRIPTION</h2>

<p>This subcommand can inspect and modify settings from Puppet's
'puppet.conf' configuration file. For documentation about individual settings,
see https://docs.puppetlabs.com/puppet/latest/reference/configuration.html.</p>

<h2 id="OPTIONS">OPTIONS</h2>

<p>Note that any setting that's valid in the configuration
file is also a valid long argument, although it may or may not be
relevant to the present action. For example, <code>server</code> and <code>run_mode</code> are valid
settings, so you can specify <code>--server &lt;servername></code>, or
<code>--run_mode &lt;runmode></code> as an argument.</p>

<p>See the configuration file documentation at
<a href="https://docs.puppetlabs.com/puppet/latest/reference/configuration.html" data-bare-link="true">https://docs.puppetlabs.com/puppet/latest/reference/configuration.html</a> for the
full list of acceptable parameters. A commented list of all
configuration options can also be generated by running puppet with
<code>--genconfig</code>.</p>

<dl>
<dt>--render-as FORMAT</dt><dd>The format in which to render output. The most common formats are <code>json</code>,
<code>s</code> (string), <code>yaml</code>, and <code>console</code>, but other options such as <code>dot</code> are
sometimes available.</dd>
<dt>--verbose</dt><dd>Whether to log verbosely.</dd>
<dt class="flush">--debug</dt><dd>Whether to log debug information.</dd>
<dt>--section SECTION_NAME</dt><dd><p>The section of the puppet.conf configuration file to interact with.</p>

<p>The three most commonly used sections are 'main', 'master', and 'agent'.
'Main' is the default, and is used by all Puppet applications. Other
sections can override 'main' values for specific applications --- the
'master' section affects puppet master and puppet cert, and the 'agent'
section affects puppet agent.</p>

<p>Less commonly used is the 'user' section, which affects puppet apply. Any
other section will be treated as the name of a legacy environment
(a deprecated feature), and can only include the 'manifest' and
'modulepath' settings.</p></dd>
</dl>


<h2 id="ACTIONS">ACTIONS</h2>

<dl>
<dt><code>print</code> - Examine Puppet's current settings.</dt><dd><p><code>SYNOPSIS</code></p>

<p>puppet config print [--section SECTION_NAME] (all | <var>setting</var> [<var>setting</var> ...]</p>

<p><code>DESCRIPTION</code></p>

<p>Prints the value of a single setting or a list of settings.</p>

<p>This action is an alternate interface to the information available with
<code>puppet &lt;subcommand> --configprint</code>.</p>

<p><code>NOTES</code></p>

<p>By default, this action reads the general configuration in the 'main'
section. Use the '--section' and '--environment' flags to examine other
configuration domains.</p></dd>
<dt><code>set</code> - Set Puppet's settings.</dt><dd><p><code>SYNOPSIS</code></p>

<p>puppet config set [--section SECTION_NAME] [setting_name] [setting_value]</p>

<p><code>DESCRIPTION</code></p>

<p>Updates values in the <code>puppet.conf</code> configuration file.</p>

<p><code>NOTES</code></p>

<p>By default, this action manipulates the configuration in the
'main' section. Use the '--section' flag to manipulate other
configuration domains.</p></dd>
</dl>


<h2 id="EXAMPLES">EXAMPLES</h2>

<p><code>print</code></p>

<p>Get puppet's runfile directory:</p>

<p>$ puppet config print rundir</p>

<p>Get a list of important directories from the master's config:</p>

<p>$ puppet config print all --section master | grep -E "(path|dir)"</p>

<p><code>set</code></p>

<p>Set puppet's runfile directory:</p>

<p>$ puppet config set rundir /var/run/puppetlabs</p>

<p>Set the vardir for only the agent:</p>

<p>$ puppet config set vardir /opt/puppetlabs/puppet/cache --section agent</p>

<h2 id="COPYRIGHT-AND-LICENSE">COPYRIGHT AND LICENSE</h2>

<p>Copyright 2011 by Puppet Inc.
Apache 2 license; see COPYING</p>

</div>
