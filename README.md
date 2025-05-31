Bu çalışma bir üniversite kampüsündeki A ve B binalarının ağ altyapısının tasarımını ve yapılandırmasını içermektedir. A ve B binaları, farklı bölümler ve cihazlar için ayrı ağlar kullanarak verimli ve güvenli bir ağ yapısı oluşturmayı amaçlamaktadır. Cisco Packet Tracer kullanılarak her binadaki cihazların yerleştirilmesi, ağ bağlantılarının sağlanması, VLAN yapılandırmalarının yapılması, IP adreslerinin atanması, DHCP yapılandırması ve routing işlemleri detaylı bir şekilde anlatılacaktır. Verilen ağ adresi 192.168.0.0/24 olup, her bir binadaki farklı ihtiyaçlara uygun alt ağlar (subnet) oluşturulacaktır.

A Binası:
A binası, idari bölüm ve sunucu bölümünden oluşmaktadır. İdari bölümde 20 bilgisayar ve bir switch bulunmakta, sunucu bölümünde ise 3 sunucu bulunmaktadır. Her bölüm için bir switch kullanılarak her cihazın kendi switchine bağlanması sağlanacaktır. Bu binada toplamda 21 cihaz bulunmaktadır.

B Binası:
B binası daha geniş bir yapıya sahiptir. Bu binada 4 departman bulunmaktadır ve her departmanda 10 bilgisayar yer almaktadır. Ayrıca, 2 bilgisayar laboratuvarı da mevcuttur ve her laboratuvarda 30 bilgisayar bulunmaktadır. Her bölüm ve laboratuvar için ayrı bir switch kullanılması gerekmektedir. B binasında toplamda 80 cihaz bulunmaktadır.
A ve B binaları arasında veri trafiğini yönlendirecek bir router bulunmaktadır. Bu routerlar arasında seri bağlantı kurularak iletişim sağlanacaktır.

Verilen ağ adresi 192.168.0.0/24’tür. Bu, toplamda 256 IP adresi sunmaktadır. Ancak, her bir bölüm ve cihaz için ayrı alt ağlar oluşturulması gerektiği için IP adres bloğunu subnetting yaparak daha küçük ağlara böleceğiz.
Aşağıda her VLAN için gerekli alt ağ hesaplamaları yapılmıştır:

A Binası – İdari VLAN (VLAN 10)
•	IP Adresi: 192.168.0.0/27
•	Subnet Mask: 255.255.255.224
•	IP Aralığı: 192.168.0.1 – 192.168.0.30
•	Ağ Geçidi (Router): 192.168.0.1
•	Kullanıcı Sayısı: 20 bilgisayar

A Binası – Sunucu VLAN (VLAN 20)
•	IP Adresi: 192.168.0.32/29
•	Subnet Mask: 255.255.255.248
•	IP Aralığı: 192.168.0.33 – 192.168.0.38
•	Ağ Geçidi (Router): 192.168.0.33
•	Kullanıcı Sayısı: 3 sunucu

B Binası – Bölüm 1 (VLAN 30)
•	IP Adresi: 192.168.0.40/28
•	Subnet Mask: 255.255.255.240
•	IP Aralığı: 192.168.0.41 – 192.168.0.54
•	Ağ Geçidi (Router): 192.168.0.41
•	Kullanıcı Sayısı: 10 bilgisayar

B Binası – Bölüm 2 (VLAN 40)
•	IP Adresi: 192.168.0.56/28
•	Subnet Mask: 255.255.255.240
•	IP Aralığı: 192.168.0.57 – 192.168.0.70
•	Ağ Geçidi (Router): 192.168.0.57
•	Kullanıcı Sayısı: 10 bilgisayar

B Binası – Bölüm 3 (VLAN 50)
•	IP Adresi: 192.168.0.72/28
•	Subnet Mask: 255.255.255.240
•	IP Aralığı: 192.168.0.73 – 192.168.0.86
•	Ağ Geçidi (Router): 192.168.0.73
•	Kullanıcı Sayısı: 10 bilgisayar

B Binası – Bölüm 4 (VLAN 60)
•	IP Adresi: 192.168.0.88/28
•	Subnet Mask: 255.255.255.240
•	IP Aralığı: 192.168.0.89 – 192.168.0.102
•	Ağ Geçidi (Router): 192.168.0.89
•	Kullanıcı Sayısı: 10 bilgisayar

B Binası – Laboratuvar 1 (VLAN 70)
•	IP Adresi: 192.168.0.104/27
•	Subnet Mask: 255.255.255.224
•	IP Aralığı: 192.168.0.105 – 192.168.0.134
•	Ağ Geçidi (Router): 192.168.0.105
•	Kullanıcı Sayısı: 30 bilgisayar

B Binası – Laboratuvar 2 (VLAN 80)
•	IP Adresi: 192.168.0.136/27
•	Subnet Mask: 255.255.255.224
•	IP Aralığı: 192.168.0.137 – 192.168.0.166
•	Ağ Geçidi (Router): 192.168.0.137
•	Kullanıcı Sayısı: 30 bilgisayar

![image](https://github.com/user-attachments/assets/426876b7-91b3-4654-84a3-413286b5227a)
Bu show vlan brief komutunun çıktısı, A switch'inde yapılandırılmış olan VLAN'ların ve her VLAN'a atanmış olan portların bir özetini sunar. 

VLAN'lar ve Bağlı Portlar:

1.	VLAN 1 (default):
VLAN 1, Cisco switch'lerinde varsayılan VLAN'dır. Bu VLAN genellikle yönetim amaçlı kullanılır ve üzerinde değişiklik yapılmadıkça tüm portlar bu VLAN'a atanır. Çıktıya göre, VLAN 1'e Fa0/21, Fa0/22, Fa0/23, Fa0/24, Gig0/1, ve Gig0/2 portları atanmıştır. Bu portlar, genel ağda kullanılmakta olan portlardır.

2.	VLAN 10 (idari):
VLAN 10, "idari" olarak adlandırılmış ve aktif durumda. Bu VLAN'a sadece Fa0/1 portu atanmış. Bu port, idari bölümdeki cihazlara (PC, yazıcı vb.) hizmet verecek şekilde yapılandırılmıştır. Bu port, VLAN 10’a ait olan cihazlar arasında iletişimi sağlar.

3.	VLAN 20 (Sunucu):
VLAN 20, "Sunucu" VLAN'ıdır ve sunucuların (server) bulunduğu VLAN'dır. Bu VLAN’a toplam 20 port atanmış ve bunlar Fa0/2 ile Fa0/20 arasındaki portlardır. Bu portlar, sunucular ve diğer ağ cihazları arasında veri iletimini sağlayan ağ yapısını oluşturur. Sunucu bölümü için ayrı bir VLAN kullanmak, ağ güvenliği ve yönetimi açısından faydalıdır çünkü sunucuların trafiği diğer cihazlardan izole edilmiştir.

4.	VLAN 1002-1005 (fddi-default, token-ring-default, fddinet-default, trnet-default):
Bu VLAN'lar, genellikle eski ağ teknolojileriyle ilişkili olup çoğunlukla varsayılan olarak konfigüre edilir ve aktif değildir. FDDI (Fiber Distributed Data Interface) ve Token Ring gibi eski ağ teknolojilerine özgü VLAN’lar olup, modern ağlarda genellikle kullanılmazlar. Ancak, Cisco switch'leri bu VLAN'ları varsayılan olarak oluşturur. Bu VLAN’lar, yalnızca eski sistemlerle uyumluluk sağlamak amacıyla bulunur.

Bu ağ tasarımı ve yapılandırması ile A ve B binaları arasındaki iletişim sağlanabilir. VLAN yapıları, farklı departmanlar ve laboratuvarlar için ayrılmıştır. DHCP yapılandırması her VLAN için IP atamasını otomatik olarak yapmaktadır. Ayrıca, yönlendirme yapılandırması ile her VLAN arasında veri trafiği iletilebilecektir.

Cisco Packet Tracer üzerinde yapılan yapılandırmalar doğrultusunda, her bir bölüm için ayrı IP aralıkları atanmış ve VLAN'lar doğru bir şekilde yapılandırılmıştır.
