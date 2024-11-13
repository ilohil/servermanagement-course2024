# H2 Infra-as-code

Tämän viikon tehtävissä tuli tiivistää viisi artikkelia sekä tehdä Vagrantilla kahden Linux-koneen verkko. Verkossa tuli toteuttaa Saltilla herra-orja arkkitehtuuri ja tehdä sls-tiedostoja, joita pystyy ajamaan verkon yli orjalla.

## Tiivistelmät

### Two Machine Virtual Network With Debian 11 Bullseye and Vagrant

- Vagrantin käyttöön pitää asentaa itse Vagrant sekä Virtualbox.
- Jos haluaa käyttää useampaa virtuaalitietokonetta Vagrantissa, tulee luoda Vagrantfile, johon määritellään luotavat virtuaalitietokoneet.
- Virtuaalikoneet voi luoda komennolla `$ vagrant up`, poistaa komennolla `$ vagrant destroy` ja haluttuun virtuaalikoneeseen voidaan kirjautua komennolla `$ vagrant ssh {virtuaalikoneen nimi}`

(Karvinen 2021)

### Salt Quickstart – Salt Stack Master and Slave on Ubuntu Linux

- Saltissa riittää, että vain master on julkisessa verkossa ja sen osoite tiedetään. Orjat voivat olla missä tahansa esimerkiksi palomuurin takana.
- Jotta Salt toimii täytyy hallinnoivalle tietokoneelle asentaa salt-master ja orjatietokoneille salt-minion.
- Lopuksi vielä orjatietokoneen salasana täytyy hyväksyä herratietokoneella.
- Tämän jälkeen orjatietokoneita voi hallinoida herratietokoneelta käsin sudo salt-komennolla.

(Karvinen 2018)

### Hello Salt Infra-as-Code

- Moduuleita voi tehdä /srv/salt kansioon, joka on jaettu kaikille orjatietokoneille. Eri moduuleille kannattaa tehdä omat kansiot.
- Moduulin sisään voi lisätä sls-tiedostoja Salt-kielellä sekä lisätä muita tarvittavia tiedostoja ja malleja.
- Tehtyjä moduuleita voi toistaa paikallisesti komennolla `$ sudo salt-call --local state.apply {moduulin nimi}`, jolloin sls-tiedostoihin kirjoitettu Salt-koodi ajetaan.

(Karvinen 2014)

### Salt Vagrant - automatically provision one master and two slaves

- Moduuleita voi toistaa kaikilla orjatietokoneilla komennolla `$ sudo salt '*' state.apply {moduulin nimi}`.
- Halutut moduulit halutuille ryhmille voidaan tallentaa top.sls-tiedostoon /srv/salt kansion alle, jolloin ne toistetaan automaattisesti ilman, että moduulin nimeä tarvii erikseen kertoa. Tällöin komennoksi riittää `$ sudo salt '*' state.apply`.

(Karvinen 2023)

### Salt overview

- Salt käyttää YAML-kieltä.
- YAML-kielessä data varastoidaan avain-arvo pareina ja avain erotetaan arvosta kaksoispisteellä. Isoilla ja pienillä kirjaimilla on merkitystä.
- Tabin käyttö ei ole sallittua, vaan esimerkiksi ominaisuudet tai listat tulee sisentää välilyönneillä. Lohkojen vakiosisennyksenä käytetään tyypillisesti kahta välilyöntiä.
- Kommentit alkavat #-merkillä.

(Salt contributors s.a.)


## Lähteet

Karvinen, T. 2014. Hello Salt Infra-as-Code. Tero Karvisen verkkosivusto. Luettavissa [https://terokarvinen.com/2024/hello-salt-infra-as-code/](https://terokarvinen.com/2024/hello-salt-infra-as-code/). Luettu: 11.11.2024.

Karvinen, T. 2018. Salt Quickstart – Salt Stack Master and Slave on Ubuntu Linux. Tero Karvisen verkkosivusto. Luettavissa: [https://terokarvinen.com/2018/03/28/salt-quickstart-salt-stack-master-and-slave-on-ubuntu-linux/](https://terokarvinen.com/2018/03/28/salt-quickstart-salt-stack-master-and-slave-on-ubuntu-linux/). Luettu: 11.11.2024.

Karvinen, T. 2023. Salt Vagrant - automatically provision one master and two slaves. Tero Karvisen verkkosivusto.  Luettavissa: [https://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-file](https://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-file). Luettu: 11.11.2024.

Karvinen, T. 2021. Two Machine Virtual Network With Debian 11 Bullseye and Vagrant. Tero Karvisen verkkosivusto. Luettavissa: [https://terokarvinen.com/2021/two-machine-virtual-network-with-debian-11-bullseye-and-vagrant/](https://terokarvinen.com/2021/two-machine-virtual-network-with-debian-11-bullseye-and-vagrant/). Luettu: 11.11.2024.

Salt Contributors. s.a. Salt overview. Salt user guide. Luettavissa: [https://docs.saltproject.io/salt/user-guide/en/latest/topics/overview.html#](https://docs.saltproject.io/salt/user-guide/en/latest/topics/overview.html#). Luettu: 13.11.2024.
