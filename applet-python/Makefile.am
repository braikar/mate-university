applet_SCRIPTS = university-python-applet
appletdir = $(libexecdir)

APPLET_LOCATION = $(libexecdir)/university-python-applet

appletsdir       = $(datadir)/mate-panel/applets
applets_in_files = org.mate.university.PythonApplet.mate-panel-applet.in
applets_DATA     = $(applets_in_files:.mate-panel-applet.in=.mate-panel-applet)

$(applets_in_files): $(applets_in_files).in Makefile
	$(AM_V_GEN)sed \
		-e "s|\@LOCATION\@|$(appletdir)|" \
		$< > $@
%.mate-panel-applet: %.mate-panel-applet.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*po) ; $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -d -u -c $(top_builddir)/po/.intltool-merge-cache

servicedir       = $(datadir)/dbus-1/services
service_in_files = org.mate.panel.applet.UniversityPythonAppletFactory.service.in
service_DATA     = $(service_in_files:.service.in=.service)

org.mate.panel.applet.UniversityPythonAppletFactory.service: $(service_in_files) Makefile
	$(AM_V_GEN)sed \
		-e "s|\@LOCATION\@|$(APPLET_LOCATION)|" \
		$< > $@

EXTRA_DIST = \
	$(applets_in_files) \
	$(service_in_files)

