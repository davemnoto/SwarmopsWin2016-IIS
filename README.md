SOFTWARE BEING REVISED
======================

**This repo is undergoing changes to resume development.** The information below is legacy and subject to change as this software clarifies its direction.


Swarmops
========

**Swarmops is a necessary tool to enable any bitcoin-native or decentralized gamechanger.**

Swarmops is an admin system for swarm-type organizations. It's a bureaucracy system for people who thoroughly dislike bureaucracy, so it removes all visibility of it and focuses on the ops aspects. It manages decentralized authority, volunteers, members, activists, budgets, mass communications, expenses, payroll, invoices, and complete financials/bookkeeping.

The goals of _Swarmops_ are three:

* Become the #1 software to manage native-bitcoin startups' cashflow and accounting,
* Become the #1 software for organizing swarm activism to effectively change policy,
* Become the #1 software to run civil liberties resistances in repressive regimes.

Goal #1, _the primary back-end software for bitcoin-native unbanked startups:_ Swarmops does bookkeeping and accounting on fully automatic. Today, there are no services or packages for bitcoin-native and unbanked organizations – for startups which are unbanked by choice. Swarmops seeks to fill that role and provide automatic accounting and cashflow management for such organizations, maintaining hot and cold wallets along with automated invoice and payroll processing. (Imagine invoices being paid on fully automatic, and not needing a €100,000 software package and a fifteen-page bank contract to do so.) There is a huge void to fill here, and Swarmops fills this role in addition to all other back-end management.

Goal #2, _organizing swarm activism:_ the Swedish Pirate Party used a predecessor to Swarmops in its effort to put two representatives in the European Parliament, and could literally not have succeeded without the ability to decentralize authority that Swarmops provided, pushing all the crucial decision-making out to the edges of the organization where the most information was available. It's an administration tool for people who hate paperwork, so it's built to optimize the time available to activism.

Goal #3, _functional software to assist civil liberties resistances in repressive regimes:_ With the swarm functions and the bitcoin-native cash flow in place, a “hidden branch” of organizations can be enabled, where nobody knows the identities of other people in the organization's “hidden branch” swarm except those closest to that individual, but where everybody is still working toward a common goal. Recruiting would take place face-to-face using mobile phones and BitID, and code names would be used for all other purposes. In this way, Swarmops enables large-scale change while able to protect the individuals involved in making that change come about. Lack of information even at the central level provides deniability against rubberhose attacks.


Release schedule
----------------

Stable releases are built every six months, in March and September. These are called YEAR.MONTH, like 2021.3, along with a release name. Sprints toward these releases are built on the 5th of every month, sometimes skipping a month when bigger features are being written. Internal builds are built all the time and can be tested at http://sandbox.swarmops.com/ which doesn't require a login.

This is the plan, at least. "Stable" is a somewhat wide definition at the moment. Rather, Swarmops has a few functions to go to enter Open Beta stage.


Installation
------------

Minimum requirements are a Windows Server 2016. Further, Mono is no longer required. The .NET Framework 4.5.2 is recommended and has native code base that can handle all the functionality of the old MONO software.

As of this writing, the software has just been branched (August 2025). Expected release date should be around January 2026.
When ready, you can download this Github repository (SwarmopsWin2016-IIS) using Visual Studio 2019 Community edition using its native Github installation routines.
```
Not sure about the need for the following commands:
sudo su
wget -qO- https://packages.swarmops.com/swarmops-packages.gpg.key | apt-key add -
apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
```


```

```


```
```
[NOTE: THE info that follows below is legacy and not to be used for this version !!!!!!!!!!! ]

Contributing
------------

No permission necessary, really. Just check in code. The backend is ASP.Net/C# and the frontend (where most of the development happens) is Javascript and jQuery. There's not really a master list beyond this one at present with tasks; getting one to work in GitHub (or GitLab) would be practical. A number of approaches have been tried, none of which have worked out in practice.

Let's take that again, because it's important: **about 90% of development happens in JavaScript and jQuery**, so don't shy away because it looks like a C# backend.

There's also a [Slack workspace](https://swarmops.slack.com) ([public invite here](https://join.slack.com/t/swarmops/shared_invite/enQtMzI1MTMwMTkyNjI4LWUwMjQxY2I3MWVkMTFjNzE5MWU5ZjEzYjZlY2UwYjk2YmNiOGQ4OWQ3NmZkMjA0NGIxY2ZlMWVlNzRjNjE4MmE)) and a Facebook group named [Swarmops Developers](https://www.facebook.com/groups/swarmops.developers/) which you may want to join. Yes, Facebook and Slack are both private, and that is bad, but until there's a better alternative, that's where discussions happen.



Translating
-----------

Use [this link](http://translate.swarmops.com/project/activizr/invite?d=65j615l6862727v4e373) to join the Swarmops project on Crowdin at the Proofreader level. There are [many languages](https://crowdin.com/project/activizr) that still need translation; any one that reaches 50% or more translated with the Menu and Global sections at 100% will be enabled from the Language Selection page.



License
-------

No, there isn't a "license". This code is completely in the public domain, with the exception of external libraries used. Those are marked as such. In jurisdictions where public domain doesn't exist as a legal concept, the code is under the CC-0 (Creative Commons Zero) license.

That also means that any code _you_ commit to Swarmops, whether by checking in code to this repository or by doing so to forks and then pushing code back here, is irrevocably committed to the public domain.


2021.3 "Ankara" release features progress
-----------------------------------------

- [x] Parameterize the bank file import procedure (big feature!)
- [x] Make it possible to import bank files in non-presentation currency
- [ ] Rewrite payment addresses (a new name for this? Account vs. designator?)
- [ ] Complete rewrite of the bank import procedure, account matching UX
- [ ] End-of-month wizard to guide user through accounting steps
- [ ] Enable payment destinations, with currency
- [ ] Rewrite Bitcoin Cold Storage detection to handle forks, current and future
- [ ] Add blockchain-upgrade code that properly splits Core, Cash txs, hashes, accounts
- [ ] Write a Pay Invoice page for Bitcoin Cash
- [ ] Tie payment identifiers to people and suppliers



Detailed install instructions
-----------------------------

This is the exact install procedure for a two-server setup. Two separate servers are strongly recommended for production use; for testing and evaluation, they can be one and the same machine.

1. Create two clean Ubuntu Xenial/Bionic or Debian Stretch machines. Call them _backend_ and _frontend._ They can be in different firewall zones. Install mysql-server on the backend (or on a third server).

2. Install the repository and its key on both machines. In the commands below, replace the "[xenial/bionic/stretch]" with just _xenial_, _bionic_, or _stretch,_ as per your distribution. Same for "[ubuntu/debian]".

```
sudo su
wget -qO- http://packages.swarmops.com/swarmops-packages.gpg.key | apt-key add -
apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
echo deb http://packages.swarmops.com/ [xenial/stretch] contrib > /etc/apt/sources.list.d/swarmops.list
echo "deb https://download.mono-project.com/repo/[ubuntu/debian] stable-[xenial/bionic/stretch] main" > /etc/apt/sources.list.d/mono-official-stable.list
apt update
```

3. Install the packages "swarmops-frontend" and "swarmops-backend", respectively, on the frontend and backend machine. Make use of as much automation on installing swarmops-frontend as you like, up to and including the autoconfiguration of Apache.

```
apt install swarmops-frontend
```

4. Open a browser and navigate to the swarmops-frontend machine, pass the first no-bot check in the install wizards, and enter database server root credentials. This will create a database and provision it with initial data, which takes a couple of minutes.

5. If you're not comfortable entering the root credentials into a random app, (optional step) run these commands as root instead at the MySQL/MariaDB prompt to create the database users with the right permissions. Replace the passwords with something of your own choosing:

```
CREATE DATABASE `Swarmops`;
CREATE USER `Swarmops-R` IDENTIFIED BY 'readpassword';
CREATE USER `Swarmops-W` IDENTIFIED BY 'writepassword';
CREATE USER `Swarmops-A` IDENTIFIED BY 'adminpassword';
GRANT SELECT ON mysql.proc TO `Swarmops-W`;
GRANT SELECT ON mysql.proc TO `Swarmops-A`;
USE `Swarmops`;
GRANT ALL ON `Swarmops`.* TO `Swarmops-A`;
GRANT SELECT ON `Swarmops`.* TO `Swarmops-W`;
GRANT EXECUTE ON `Swarmops`.* TO `Swarmops-W`;
GRANT SELECT ON `Swarmops`.* TO `Swarmops-R`;
FLUSH PRIVILEGES;
```

We're using three different users with different privilege sets (read, write, admin) for security purposes; most operations are made using the read-only user, and only database maintenance is done using the account with all privileges. Do note the granting of `select` privileges on `mysql.proc` for the write and admin user accounts; this is necessary to execute stored procedures because of a design decision way back in MySQL's history.

This will allow you to use the manual account settings in the setup, which is more complicated as you need to fill in twelve fields instead of two, but also doesn't require you to give the webpage the database root password.

6. The installation will pause here and wait for the backend to come online. This is done by manually copying the now-created `/etc/swarmops/database.config` file from the frontend to the same location on the backend machine.

7. As the backend daemon detects the presence of a valid `/etc/swarmops/database.config` file, it will open the database (using the credentials of the file - make sure they're also valid for the backend machine, if you're using machine-level permissions!) and write its presence into the database.

8. The installing frontend process will detect this new entry in the database and proceed to a prompt to create the first user. On entering the credentials, it will login as that user into the Sandbox organization, and the Swarmops instance is operational.

9. From the Dashboard, the Apache will open a websocket to a daemon running on its own machine on port 12172, and that daemon will in turn open a websocket to the backend daemon on port 10944 (configurable in Admin / System-Wide Settings).

10. From there, one can play around with the Sandbox organization, or create one or more live organizations.


If one of these steps fails, in particular if the frontend doesn't get to provision the entire database and bring the first user logged in to the Swarmops Desktop, it is currently recommended to restart from two blank servers. Future code will handle more failure scenarios.

