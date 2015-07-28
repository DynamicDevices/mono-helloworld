helloworlddir=$(pkglibdir)

helloworld_SCRIPTS = helloworld.exe
EXTRA_DIST = $(helloworld_sources) $(helloworld_sources_in)

if BUILD_WINFORMDEMO
helloworld_SCRIPTS += helloworldform.exe
EXTRA_DIST += $(helloworldform_sources) $(helloworldform_sources_in) 
endif

if BUILD_GTKDEMO
helloworld_SCRIPTS += helloworldgtk.exe
EXTRA_DIST +=  $(helloworldgtk_sources) $(helloworldgtk_sources_in)
endif

CLEANFILES = helloworld.exe helloworldform.exe helloworldgtk.exe

helloworld_sources_in = AssemblyInfo.cs.in
helloworld_generated_sources = $(helloworld_sources_in:.in=)
helloworld_sources = helloworld.cs

helloworldform_sources_in = AssemblyInfo.cs.in
helloworldform_generated_sources = $(helloworldform_sources_in:.in=)
helloworldform_sources = helloworldform.cs

helloworldgtk_sources_in = AssemblyInfo.cs.in
helloworldgtk_generated_sources = $(helloworldgtk_sources_in:.in=)
helloworldgtk_sources = helloworldgtk.cs

helloworld_build_sources = $(addprefix $(srcdir)/, $(helloworld_sources))
helloworld_build_sources += $(helloworld_generated_sources)

helloworldform_build_sources = $(addprefix $(srcdir)/, $(helloworldform_sources))
helloworldform_build_sources += $(helloworldform_generated_sources)

helloworldgtk_build_sources = $(addprefix $(srcdir)/, $(helloworldgtk_sources))
helloworldgtk_build_sources += $(helloworldgtk_generated_sources)

resources = $(srcdir)/../resources/dummy.txt

embedded= $(foreach res,$(resources), $(addprefix -resource:,$(res)),$(notdir $(res)))

helloworld.exe: $(helloworld_build_sources) $(resources)
	$(MCS) $(embedded) -out:$@ $< 

helloworldform.exe: $(helloworldform_build_sources) $(resources)
	$(MCS) -r:System.Windows.Forms -r:System.Data -r:System.Drawing  $(embedded) -out:$@ $< 

helloworldgtk.exe: $(helloworldgtk_build_sources) $(resources)
	$(MCS) $(GTKSHARP_LIBS) -pkg:gtk-sharp-2.0 -r:System.Windows.Forms -r:System.Data -r:System.Drawing  $(embedded) -out:$@ $< 

