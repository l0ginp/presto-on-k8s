FROM prestosql/presto:329

# copy local connector into container
COPY etc/catalog /tmp

# copy temp into default catalog
RUN cp -a /tmp/. /usr/lib/presto/default/etc/catalog/

# run presto script
CMD ["/usr/lib/presto/bin/run-presto"]