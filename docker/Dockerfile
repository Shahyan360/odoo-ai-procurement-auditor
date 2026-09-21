ARG ODOO_IMAGE
FROM ${ODOO_IMAGE}
USER root
RUN python3 -m pip install --break-system-packages pydantic==2.12.3
USER odoo
