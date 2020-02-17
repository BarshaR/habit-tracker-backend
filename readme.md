# Setup

## Fedora 31

1. Install the JAVA 11 JDK

```

sudo dnf install java-11-openjdk-devel.x86_64
```
To verify, run `which java`, it should be the default `/usr/bin/java`

2. Add the following to your ~/.bashrc

```
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-11.0.5.10-0.fc31.x86_64/
export PATH=$JAVA_HOME/bin:$PATH
```
To verify, run `source ~/.bashrc && which java`, it should point to the new JDK e.g /usr/lib/jvm/java-11-openjdk-11.0.5.10-0.fc31.x86_64/

3. Install Jmods to work with VS code
```
sudo dnf install java-11-openjdk-jmods.x86_64
```

4. Install postgres server
```
sudo dnf install postgresql-server postgresql-contrib

# Enable postgres on boot
sudo systemctl enable postgresql

# Start postgresql server
systemctl start postgresql

# Modify the existing lines <postgres_install_dir>/data/pg_hba.conf to allow connections from localhost
# "local" is for Unix domain socket connections only

## Original
local   all             all                                     ident
# IPv4 local connections:
host    all             all             127.0.0.1/32            ident

## Modified
local   all             all                                     trust
# IPv4 local connections:
host    all             all             127.0.0.1/32            trust

```

5. Create database and database user

6. Seed the database

