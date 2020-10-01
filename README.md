Minimum Reproducer
==================

Exposes some sort of problem with molecule + ansible + tox that I have not
been able to sort out yet.

* Clone this repository
* Install tox
* Run `tox -e py38`

On systems I have been able to test, when tox attempts to run molecule from
inside of the created virtualenv, it produces this warning and error:

<pre>    TASK [Destroy molecule instance(s)] \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*
<font color="#75507B"><b>[WARNING]: Skipping plugin (/home/greg/src/ansible_collections/devroles/min_rep</b></font>
<font color="#75507B"><b>roducer/.tox/py38/lib/python3.8/site-</b></font>
<font color="#75507B"><b>packages/molecule/provisioner/ansible/plugins/filter/molecule_core.py) as it</b></font>
<font color="#75507B"><b>seems to be invalid: The &apos;ansible_base&apos; distribution was not found and is</b></font>
<font color="#75507B"><b>required by the application</b></font>
<font color="#CC0000">fatal: [localhost]: FAILED! =&gt; {&quot;msg&quot;: &quot;An unhandled exception occurred while templating &apos;{{ lookup(&apos;file&apos;, molecule_file) | molecule_from_yaml }}&apos;. Error was a &lt;class &apos;ansible.errors.AnsibleError&apos;&gt;, original message: template error while templating string: no filter named &apos;molecule_from_yaml&apos;. String: {{ lookup(&apos;file&apos;, molecule_file) | molecule_from_yaml }}&quot;}</font>
</pre>

However, a quick look at this shows that it is not true at all:

```bash
$ pip list | head -4
Package           Version
----------------- ---------
ansible           2.10.0
ansible-base      2.10.1
```
