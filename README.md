# agent

    compile files("${System.getenv('JAVA_HOME')}/lib/tools.jar")

//vm options: -Djdk.attach.allowAttachSelf=true (runtime loading)
		//-javaagent:untitled.jar (commandline argument loading)
    
    
    // runtim loading the agent:
    String nameOfRunningVM = ManagementFactory.getRuntimeMXBean().getName();
		String pid = nameOfRunningVM.substring(0, nameOfRunningVM.indexOf('@'));
		VirtualMachine vm = VirtualMachine.attach(pid);
		vm.loadAgent("untitled.jar", null);
		vm.detach();
