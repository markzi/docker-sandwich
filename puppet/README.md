# Puppet In Docker

## Puppet Server
    docker run --name puppet \
      --hostname puppet \
      -p 8140:8140 \
      -v /code:/etc/puppetlabs/code/ \
      -v /puppet/ssl:/etc/puppetlabs/puppet/ssl \
      -v /puppet/serverdata:/opt/puppetlabs/server/data/puppetserver/ \
      puppet/puppetserver

## Puppet DB Postgres

    docker run --name postgres \
      -e "POSTGRES_PASSWORD=puppetdb" \
      -e "POSTGRES_USER=puppetdb"  \
      --expose 5432 \
      -v /puppetdb-postgre/data:/var/lib/postgresql/data/ \
      -d  \
      puppet/puppetdb-postgres

## Puppet DB
    docker run --name puppetdb \
      --hostname puppetdb \
      -v /puppetdb/ssl:/etc/puppetlabs/puppet/ssl/ \
      -p 8080:8080 \
      -p 8081:8081 \
      -d  \
      puppet/puppetdb

## Puppet Board

    docker run --name puppetboard \
      -p 8000:8000 \
      -d  \
      puppet/puppetboard

## Puppet Explorer

    docker run --name puppetexplorer \
      -p 80:80 \
      -d  \
      puppet/puppetexplorer
