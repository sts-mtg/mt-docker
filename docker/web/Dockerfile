FROM centos:7
RUN yum install httpd httpd-devel -y
RUN yum install mysql-devel -y
RUN yum install -y php perl gcc \
         libxml2-dev \
         libssl-dev \
         libexpat1-dev \
         make \
         zip \
         wget \
         cpan \
         make \
         perl-HTML-Parser \
         perl-Digest-MD5 \
         perl-DBD-MySQL \
         perl-Net-SSLeay.x86_64 \
         perl-XML-LibXML.x86_64 \
         ImageMagick-perl.x86_64 \
         perl-File-Which.noarch \
         perl-Crypt-SSLeay

RUN curl -L http://cpanmin.us | perl - App::cpanminus
RUN cpanm CGI CGI::Cookie parent \
         HTML::Entities \
         Scalar::Util \
         CGI::PSGI \
         Archive::Tar \
         Image::Size \
         LWP::UserAgent \
         DBI

ENV PERL5LIB /var/www/html/local/lib/perl5

RUN chown -R apache:apache /var/www/html/
RUN chmod -R 755 /var/www/html
EXPOSE 80

CMD ["httpd", "-DFOREGROUND"]
