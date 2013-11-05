helloworlddir=$(pkglibdir)
helloworld_SCRIPTS = helloworld.exe
EXTRA_DIST = $(helloworld_sources) $(helloworld_sources_in)
CLEANFILES = helloworld.exe helloworldform.exe

helloworld_sources_in = AssemblyInfo.cs.in
helloworld_generated_sources = $(helloworld_sources_in:.in=)
helloworld_sources = helloworld.cs

helloworldform_sources_in = AssemblyInfo.cs.in
helloworldform_generated_sources = $(helloworld_sources_in:.in=)
helloworldform_sources = helloworldform.cs

helloworld_build_sources = $(addprefix $(srcdir)/, $(helloworld_sources))
helloworld_build_sources += $(helloworld_generated_sources)

helloworldform_build_sources = $(addprefix $(srcdir)/, $(helloworldform_sources))
helloworldform_build_sources += $(helloworldform_generated_sources)

resources = $(srcdir)/../resources/dummy.txt

embedded= $(foreach res,$(resources), $(addprefix -resource:,$(res)),$(notdir $(res)))

helloworld.exe: $(helloworld_build_sources) $(resources)
	$(MCS) $(GTKSHARP_LIBS) $(embedded) -out:$@ $< 
	$(MCS) $(GTKSHARP_LIBS) $(embedded) -out:$@ $< 


