FROM xqdocker/ubuntu-nginx
COPY nginx.conf /etc/nginx/nginx.conf

RUN mkdir -p /var/www/account/html \
    && mkdir -p /var/www/payroll/html

COPY index.account.html /var/www/account/html/index.html
COPY index.payroll.html /var/www/payroll/html/index.html

COPY account /etc/nginx/sites-available/account
COPY payroll /etc/nginx/sites-available/payroll

RUN ln -s /etc/nginx/sites-available/account /etc/nginx/sites-enabled/ \
    && ln -s /etc/nginx/sites-available/payroll /etc/nginx/sites-enabled/
	
RUN openssl genrsa -out /opt/kidpayroll.key 2048 \
	&& openssl req -new -x509 -key /opt/kidpayroll.key -out /opt/kidpayroll.cert -days 3650 -subj /CN=itcorpz.lv/CN=*.itcorpz.lv