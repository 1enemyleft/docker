FROM httpd:2.4

#install software
RUN apt-get update --fix-missing; \
	apt-get install -f; \
	apt-get update && apt-get install -y --fix-missing\
  	build-essential \
  	cpanminus \
  	vim \
  	wget \
	libwww-perl \
	freetds-dev \
	libdbd-sybase-perl


#perl modules
RUN cpanm --force CGI \
  DBI \
  Date::Manip \
  Mail::Mailer \
  URI::Escape \
  Math::Random \
  SOAP::Lite \
  ExtUtils::MakeMaker \
  XML::Parser \
  LWP \
  Sort::Fields \
  Statistics::LineFit \
  Statistics::Distributions \
  Statistics::Standard_Normal \
  List::BinarySearch

#replace default apache config
ADD configs/httpd.conf /usr/local/apache2/conf/httpd.conf

#expose port 80
EXPOSE 80

RUN mkdir -p /var/www ; \
	ln -s /usr/local/apache2/cgi-bin /var/www/cgi-bin ; \
	ln -s /usr/local/apache2/html /var/www/html ; \
	ln -s /usr/local/apache2/icons /var/www/icons 

#default command
CMD httpd-foreground

