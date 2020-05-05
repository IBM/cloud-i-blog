# Automate your IBM i tasks with Ansible

<p class="MsoNormal">
	<span style="font-family:Times;">Automate your IBM
i tasks with Ansible</span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">Ansible is a
radically simple IT automation system. It handles configuration management,
application deployment, cloud provisioning, ad-hoc task execution, network
automation, and multi-node orchestration. IBM i is an operating system that has
thousands of core workloads running for different industries worldwide. More
and more IBM i customers plan or have already started the journey of automating
tasks and moving workloads into cloud environment. Traditional IBM i MSPs and
ISVs are also looking for better solutions to improve the efficiency of system
and application management. Ansible for IBM i can fit most of the tasks and
cloud automation requirements for IBM i customers. </span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">There are several
cases that IBM i customers or ISVs can take advantage of Ansible:</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:-18.0pt;">
	<span style="font-family:Times;"><span>1.<span>&nbsp;&nbsp;&nbsp;&nbsp; </span></span></span><span style="font-family:Times;">Automate
traditional IBM i administration tasks, such as PTF management, system and
application configuration, application deployment and installation, etc. These
tasks are very common and are repeatedly executed in users’ environment. Thus,
automate such tasks and processes can highly improve the system management
efficiency. </span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:-18.0pt;">
	<span style="font-family:Times;"><span>2.<span>&nbsp;&nbsp;&nbsp;&nbsp; </span></span></span><span style="font-family:Times;">Improve
application development process and efficiency to shorten software delivery
cycle. Continuous integration and continuous delivery are mentioned more and
more by IBM i customers, who highly need tools to bring RPG written PGMs and
object based applications into CI/CD world. </span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:-18.0pt;">
	<span style="font-family:Times;"><span>3.<span>&nbsp;&nbsp;&nbsp;&nbsp; </span></span></span><span style="font-family:Times;">Manage
multiple IBM i systems with interactive command lines. A single place to manage
all the Linux (or other platforms) and IBM i partitions together becomes more
and more important for MSPs and cloud users. There are many cases that IT
environments and solutions are built upon many different systems so that the
central management of these systems is very important. Ansible supports
different platforms and the workflow could be managed all by playbook written
in YAML. With playbook, complex IT environment can be managed from a single
place. </span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:-18.0pt;">
	<span style="font-family:Times;"><span>4.<span>&nbsp;&nbsp;&nbsp;&nbsp; </span></span></span><span style="font-family:Times;">Automate
IBM i tasks with reusable playbooks. There are several cases that existing
playbooks can be reused for IBM i customers. For example, for the tasks dealing
with open source software in PASE, playbooks written for AIX platform may be
reused with little modifications in some situations. </span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:-18.0pt;">
	<span style="font-family:Times;"><span>5.<span>&nbsp;&nbsp;&nbsp;&nbsp; </span></span></span><span style="font-family:Times;">Ansible
is already being operated by a certain group. And the operator with no IBM i
skills wants to do basic management works of IBM i via Ansible. Ansible
developers also can use IBM i modules to complete their playbook writing even
if they may not have enough IBM i skills. </span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">Introduce IBM i
modules of Ansible</span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">The support of
Ansible for IBM i focuses on the module functions. In this case, the Ansible
engine needs to be installed on Linux servers and IBM i systems are managed as
endpoints. Some of the Ansible core modules can work with IBM i PASE
environment very well already. For example, copy and fetch modules of Ansible
can be used to copy and fetch stream files to and from IBM i systems. Ansible
module ‘command’ can also be used to execute PASE commands. However, for most
of IBM i customers , the native IBM i environment, which is object based and
managed by CL commands, running COBOL and RPG programs, is much more important.
Previously, there was no module written for IBM i native environment. IBM
started to provide IBM i modules from 2020, 1H. These modules can be found from
GitHub<span>&nbsp; </span><a href="https://github.ibm.com/IBMi-Cloud/ansible-for-i/">https://github.ibm.com/IBMi-Cloud/ansible-for-i/</a> . Although now these Ansible modules are still in BETA version, you can start to
try them out for your early testing or proof of concept. The GA version of IBM i
modules will come out in the coming months. Moreover, this repository supports
Ansible Tower so that the modules, plug-ins and playbooks can be directly
loaded to Ansible Tower through the GUI. There will be an example in later
sections of this article.</span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">The following table
lists the current IBM i modules in the GitHub repository. More modules will be
added throughout this year. <span>&nbsp;</span></span>
</p>
<table class="MsoNormalTable ke-zeroborder" cellpadding="0" border="0">
	<tbody>
		<tr>
			<td>
				<p class="MsoNormal" style="text-align:left;" align="left">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_at.py">ibmi_at</a> </span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Schedule a
  batch job on a remote IBMi node. </span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_cl_command.py">ibmi_cl_command</a> </span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Executes a CL
  command. </span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_copy.py">ibmi_copy</a> </span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Copy a save
  file from local to a remote IBMi node. </span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_display_subsystem.py">ibmi_display_subsystem</a> </span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Display all
  currently active subsystems or currently active jobs in a subsystem. </span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_end_subsystem.py">ibmi_end_subsystem</a> </span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">End a
  subsystem. </span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_fetch.py">ibmi_fetch</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Fetch objects
  or a library from a remote IBMi node and store on local.</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_install_product_from_savf.py">ibmi_install_product_from_savf</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Install the the
  licensed program(product) from a save file.</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_lib_restore.py">ibmi_lib_restore</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Restore one
  library on a remote IBMi node.</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_lib_save.py">ibmi_lib_save</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Save one libary
  on a remote IBMi node.</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_object_authority.py">ibmi_object_authority</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Grant, Revoke
  and Display the Object Authority.</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_object_restore.py">ibmi_object_restore</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Restore one or
  more objects on a remote IBMi node.</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_object_save.py">ibmi_object_save</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Save one or
  more objects on a remote IBMi node.</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_reboot.py">ibmi_reboot</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Reboot IBMi
  machine.</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_save_product_to_savf.py">ibmi_save_product_to_savf</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Save the the
  licensed program(product) to a save file.</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_script.py">ibmi_script</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Execute a local
  cl/sql script file on a remote ibm i node. </span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_script_execute.py">ibmi_script_execute</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Execute a
  cl/sql script file on a remote ibm i node.</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_sql_execute.py">ibmi_sql_execute</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Executes a SQL
  non-DQL(Data Query Language) statement.</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_sql_query.py">ibmi_sql_query</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Executes a SQL
  DQL(Data Query Language) statement.</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_start_subsystem.py">ibmi_start_subsystem</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Start a subsystem.</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_sync.py">ibmi_sync</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Synchronize a
  save file from current ibm i node A to another ibm i node B.</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_synchronize.py">ibmi_synchronize</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Synchronize a
  save file from ibm i node A to another ibm i node B.</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_uninstall_product.py">ibmi_uninstall_product</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Delete the
  objects that make up the licensed program(product).</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_user_and_group.py">ibmi_user_and_group</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Create, Change
  and Display a user(or group) profile.</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_device_vary.py">ibmi_device_vary</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Vary on or off
  target device on a remote IBMi node</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_host_server_service.py">ibmi_host_server_service</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Manage host
  server on a remote IBMi node</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_tcp_server_service.py">ibmi_tcp_server_service</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Manage tcp
  server on a remote IBMi node</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_iasp.py">ibmi_iasp</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Control IASP on
  target IBMi node</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_message.py">ibmi_message</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Search or reply
  message on a remote IBMi node</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_fix.py">ibmi_fix</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Load from save
  file, apply, remove or query PTF(s). </span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_fix_imgclg.py">ibmi_fix_imgclg</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Install fixes
  from virtual image.</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_job.py">ibmi_job</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Returns job
  information per user request.</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_object_find.py">ibmi_object_find</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Find specific
  IBM i object(s).</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_submit_job.py">ibmi_submit_job</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Submit an IBM i
  job.</span>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/lib/ansible/modules/ibmi/ibmi_tcp_interface.py">ibmi_tcp_interface</a></span>
				</p>
			</td>
			<td>
				<p class="MsoNormal">
					<span style="font-family:Times;">Manage IBM i TCP
  interface. You can add, remove, start, end or query a TCP interface.</span>
				</p>
			</td>
		</tr>
	</tbody>
</table>
<p class="MsoNormal">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">As mentioned previously
in this article, some of the Ansible core modules can support IBM i. These modules
are not developed specifically for IBM i and such modules can be divided into
two categories. One category of modules controls the working flow of the Ansible
playbook running, and they can be used for all the IBM i tasks. For example,
the wait_for_connection module controls the playbook to wait for the endpoint connection
being set up. The other category can run the tasks under IBM i PASE. For
example, the command module can run tasks with PASE commands. </span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">The following
table lists the core modules that can be used for IBM i tasks. Please note
that, these modules only passed sanity tests from IBM i development team. There
is future plan to do full testing for these modules in the coming months. </span>
</p>
<table class="MsoTableGrid" style="border-collapse:collapse;border:none;" cellspacing="0" cellpadding="0" border="1">
	<tbody>
		<tr>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">command</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">script</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">set_up</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">copy</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">fetch</span>
				</p>
			</td>
		</tr>
		<tr>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">file</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">find</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">stat</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">synchronize</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">raw</span>
				</p>
			</td>
		</tr>
		<tr>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">shell</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">pip</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">yum</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">pause</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">ping</span>
				</p>
			</td>
		</tr>
		<tr>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">wait_for_connection</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">authorized_key</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">assemble</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">blockinfile</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">lineinfile</span>
				</p>
			</td>
		</tr>
		<tr>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">git</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">&nbsp;</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">&nbsp;</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">&nbsp;</span>
				</p>
			</td>
			<td style="border:solid windowtext 1.0pt;" width="111" valign="top">
				<p class="MsoNormal">
					<span style="font-family:Times;">&nbsp;</span>
				</p>
			</td>
		</tr>
	</tbody>
</table>
<p class="MsoNormal">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">More about
Ansible for IBM i GitHub repository. </span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">Currently, all the
Ansible for IBM i modules, plugins and samples can be found via the link <a href="https://github.ibm.com/IBMi-Cloud/ansible-for-i/">https://github.ibm.com/IBMi-Cloud/ansible-for-i/</a>.
You may want to start with the README for detail information including an
installation guide. </span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">With the
supported IBM i modules and Ansible core modules, common IBM i tasks can all be
done by Ansible. Here give some examples of how to use Ansible modules for IBM
i. </span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:-18.0pt;">
	<span style="font-family:Times;"><span>1.<span>&nbsp;&nbsp;&nbsp;&nbsp; </span></span></span><span style="font-family:Times;">Prepare
your environment.</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">Before you can successfully run
your first Ansible task, you need to make sure that your environment is ready.
This means that your Ansible engine system and IBM i systems to be managed should
both meet the certain environment requirements. You need to follow the README
of the Ansible for IBM i GitHub repository for dependency checking and
installation guide. </span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">After your environment is ready,
the first thing to do is to configure IBM i inventory. For Ansible engine, inventory
information could be configured into configuration file. For more information
about Ansible inventory, please check out this link: <a href="https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html">https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html</a>.
Here is a sample file content of the IBM i inventory:</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;">[ibmi]</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;">9.5.xxx.yyy ansible_ssh_user=youribmiuser
ansible_ssh_pass=yourpassword</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;">[ibmi:vars]</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;">ansible_python_interpreter="/QOpensys/pkgs/bin/python2"</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;">ansible_ssh_common_args='-o
StrictHostKeyChecking=no'</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoNormal" style="text-indent:21.0pt;">
	<span style="font-family:Times;">In the above section of configuration file, a group named
‘ibmi’ has been created and there is only one system under that group. Also, the
variables against group ibmi have been defined in the file. One important variable
is ansible_python_interpreter which tells Ansible where to find Python on the
endpoint IBM i system in group ibmi. You</span>
</p>
<p class="MsoNormal" style="text-indent:21.0pt;">
	<span style="font-family:Times;">If you use Ansible Tower, you will have to do all the
inventory configurations via the GUI.</span>
</p>
<p class="MsoNormal" style="text-indent:21.0pt;">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:-18.0pt;">
	<span style="font-family:Times;"><span>2.<span>&nbsp;&nbsp;&nbsp;&nbsp; </span></span></span><span style="font-family:Times;">Run
Ansible command interactively using ibmi_cl_command module.</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">In this example, we will run a simple
IBM i module named ibmi_cl_command interactively in the command terminal. The
module will execute a CL command which creates a library of C1 on the system
under inventory ibmi. As you can see from below command, option -i and -M are explicitly
used to point out the inventory path and the IBM i module directory. You don’t
need to use these two options if you have put the inventory and IBM i modules
into Ansible default locations.</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;">ansible ibmi -i /yourpath/hosts_ibmi.ini -M
/yourmodulepath/ibmi/ -m ibmi_cl_command -a "cmd='crtlib lib(C1)'"</span><span style="font-family:Times;"></span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;">Output:</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;">DB2MB1PA.RCH.STGLABS.IBM.COM | SUCCESS =&gt; {</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;"><span>&nbsp;&nbsp;&nbsp; </span>"changed": false,</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;"><span>&nbsp;&nbsp;&nbsp; </span>"cmd": "crtlib lib(C2)",</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;"><span>&nbsp;&nbsp;&nbsp; </span>"delta": "0:00:00.386441",</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;"><span>&nbsp;&nbsp;&nbsp; </span>"end": "2019-12-11 11:55:42.627733",</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;"><span>&nbsp;&nbsp;&nbsp; </span>"joblog": false,</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;"><span>&nbsp;&nbsp;&nbsp; </span>"rc": 0,</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;"><span>&nbsp;&nbsp;&nbsp; </span>"rc_msg": "Success",</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;"><span>&nbsp;&nbsp;&nbsp; </span>"start": "2019-12-11 11:55:42.241292",</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;"><span>&nbsp;&nbsp;&nbsp; </span>"stderr": "",</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;"><span>&nbsp;&nbsp;&nbsp; </span>"stderr_lines": [],</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;"><span>&nbsp;&nbsp;&nbsp; </span>"stdout": "CPC2102: Library C1 created.\n",</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;"><span>&nbsp;&nbsp;&nbsp; </span>"stdout_lines": [</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span>"CPC2102: Library C1 created."</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;"><span>&nbsp;&nbsp;&nbsp; </span>]</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">}</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">If you want to see the detail
parameters that are supported by a particular module, you could use ansible-doc
command. In this example, you could issue below command to get all the
parameters supported by ibmi_cl_command module:</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-size:8.0pt;font-family:Menlo;color:black;">ansible-doc -s -M /yourmodulepath/ibmi/ ibmi_cl_command</span>
</p>
<p class="MsoNormal" style="text-align:left;" align="left">
	<span style="font-size:11.0pt;font-family:Menlo;color:black;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></span><span style="font-size:8.0pt;font-family:Menlo;color:black;">-
name: Executes a CL command on a remote IBM i node</span>
</p>
<p class="MsoNormal" style="text-align:left;" align="left">
	<span style="font-size:8.0pt;font-family:Menlo;color:black;"><span>&nbsp; </span><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>ibmi_cl_command:</span>
</p>
<p class="MsoNormal" style="text-align:left;" align="left">
	<span style="font-size:8.0pt;font-family:Menlo;color:black;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span>&nbsp;&nbsp;&nbsp;</span>asp_group:<span>&nbsp; </span># Specifies the name of the auxiliary storage
pool (ASP) group to set for the current thread. The ASP group name is the name
of the primary ASP device within the ASP group.</span>
</p>
<p class="MsoNormal" style="text-align:left;" align="left">
	<span style="font-size:8.0pt;font-family:Menlo;color:black;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span>&nbsp;&nbsp;&nbsp;</span>cmd:<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span># (required) The IBM i CL command to
run.</span>
</p>
<p class="MsoNormal">
	<span style="font-size:8.0pt;font-family:Menlo;color:black;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span>joblog:<span>&nbsp;&nbsp;&nbsp;&nbsp; </span><span>&nbsp;</span># If set to `true', append JOBLOG to
stderr/stderr_lines.</span><span style="font-size:6.5pt;font-family:Times;"></span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">More examples can be found in GitHub
repository: <a href="https://github.com/IBM/ansible-for-i/blob/master/examples/ibmi/samples.txt">https://github.com/IBM/ansible-for-i/blob/master/examples/ibmi/samples.txt</a></span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:-18.0pt;">
	<span style="font-family:Times;"><span>3.<span>&nbsp;&nbsp;&nbsp;&nbsp; </span></span></span><span style="font-family:Times;">Run a
simple Ansible playbook.</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">The Ansible playbook is used to
run a list of tasks executed by modules. IBM i modules can be used together
with other Ansible modules to complete complex tasks. Here is a simple example
to demonstrate how to write playbook for IBM i systems. </span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;">---</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;">- hosts: ibmi</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;"><span>&nbsp; </span>gather_facts: no</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;"><span>&nbsp; </span>tasks:</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;"><span>&nbsp; </span>- name:
run the CL command to create a library</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;">
	<span style="font-family:Times;"><span>&nbsp;&nbsp;&nbsp; </span>ibmi_cl_command:</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></span><span style="font-family:Times;"><span>&nbsp;&nbsp;&nbsp;&nbsp;</span></span><span style="font-family:Times;">cmd: crtlib lib(ansiblei)</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">Once you have your playbook
written, you can use ansible-playbook command to run the playbook. Similar to ‘ansible’
command, you could specify the path to IBM i modules and inventory if you don’t
want to use the default locations.</span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span>ansible-playbook -i
/yourpath/hosts_ibmi.ini -M /yourmodulepath/ ibmi-cl-command-sample.yml</span><span style="font-family:Times;"></span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">For more information about
Ansible playbook, please refer to the link here: </span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;"><a href="https://docs.ansible.com/ansible/latest/user_guide/playbooks.html">https://docs.ansible.com/ansible/latest/user_guide/playbooks.html</a><span class="MsoHyperlink"></span></span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">In the Ansible for IBM i GitHub
repository, there are several playbook samples provided in the link here: </span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;"><a href="https://github.com/IBM/ansible-for-i/tree/master/examples/ibmi/playbooks">https://github.com/IBM/ansible-for-i/tree/master/examples/ibmi/playbooks</a> </span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">In the repository, there are IBM i
module test cases in the format of playbooks as well. You could refer to them as
more examples as well.</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:-18.0pt;">
	<span style="font-family:Times;"><span>4.<span>&nbsp;&nbsp;&nbsp;&nbsp; </span></span></span><span style="font-family:Times;">Run IBM
i modules and playbooks with Ansible Tower. </span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">In the Ansible for IBM i
repository, there is a sample playbook ibmi_try_tower_structure.yml in the root
directory that you could use in your Ansible Tower template. The repository
structure supports creating Ansible Tower project. Here are some key steps showing
you where to config the GitHub repository to load the modules and playbooks.</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">The assumption here is that the inventory
and credential are all configured already. When creating a new project, you
could specify the SCM TYPE as Git and fill the Ansible for IBM i GitHub repository
link in SCM URL field. ‘master’ branch is used in this example.</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;"><img src="file://Users/autoair/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image001.png" width="565" height="341" border="0" /></span><span style="font-family:Times;"></span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoListParagraph" style="margin-left:18.0pt;text-indent:0cm;">
	<span style="font-family:Times;">After the project has been
created, you need to define Template to run particular tasks. In the Template, you
need to select the playbook from drop down menu of PLAYBOOK option. The list of
playbook files are automatically loaded from GitHub repository. </span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;"><img src="file://Users/autoair/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image002.png" alt="A screenshot of a cell phone Description automatically generated" width="675" height="256" border="0" /></span><span style="font-family:Times;"></span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">You could launch
the tasks when everything is configured. </span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;"><img src="file://Users/autoair/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image003.png" alt="A screenshot of a social media post Description automatically generated" width="699" height="370" border="0" /></span><span style="font-family:Times;"></span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">&nbsp;</span>
</p>
<p class="MsoNormal">
	<span style="font-family:Times;">To summarize, with
IBM i modules, Ansible is perfect for your automation work for both on-prem and
cloud environment. </span>
</p>
