# © Copyright IBM Corporation 2016.
#
# All rights reserved. This program and the accompanying materials
# are made available under the terms of the Eclipse Public License v1.0
# which accompanies this distribution, and is available at
# http://www.eclipse.org/legal/epl-v10.html

FROM sg248351/stub
MAINTAINER Carsten Bornert carsten.bornert@uk.ibm.com

RUN rm /bin/sh && ln -s /bin/bash /bin/sh
ADD CatalogService.bar /tmp/CatalogService.bar
ADD CatalogService.overrides /tmp/CatalogService.overrides
ADD Products.xml /tmp/products.xml

ENV BASH_ENV=/usr/local/bin/iib_env.sh

RUN bash && source /opt/ibm/iibruntime/server/bin/mqsiprofile && mqsistart node1 && sleep 3 && \
    mqsiapplybaroverride -b /tmp/CatalogService.bar -p /tmp/CatalogService.overrides -r && \
    mqsideploy node1 -e default -a /tmp/CatalogService.bar
