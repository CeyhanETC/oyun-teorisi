import random
import time
import os
os.system('cls' if os.name == 'nt' else 'clear')

puan = 0
yapayZekaPuan = 0

rakipSecim=input("Normal Yapay Zeka mı Duygusal Yapay Zeka mı yoksa karakter mi (normal/duygusal/karakter)?: ")

if rakipSecim.lower()=="normal":
    for game in range(10):   
        secim = input("Kazık/İşbirliği: ")
        yapayZekaSecim = random.randint(0,1)

        match yapayZekaSecim:
            case 1:
                print("işbirlik")
            case 0:
                print("Kazık")

        if yapayZekaSecim == 1:  # işbirliği
            if secim.lower() == "kazık":
                puan += 3
                yapayZekaPuan -= 1
            else:
                puan += 2
                yapayZekaPuan += 2
        else:  # kazık
            if secim.lower() == "kazık":
                puan += 0          
                yapayZekaPuan += 0
            else:
                puan -= 1
                yapayZekaPuan += 3
    time.sleep(1)
    print("Senin puanın: ",puan)
    print("Rakibin puanı: ", yapayZekaPuan)
    if yapayZekaPuan > puan:
        print("Rakip yendi.")
    elif puan > yapayZekaPuan:
        print("Sen yendin. ")
    else:
        print("Berabere")

elif rakipSecim.lower()=="duygusal":
    yapayZekaSecim=random.randint(-1,2)
    for game in range(5):  
        secim = input("Kazık/İşbirliği: ")
        match yapayZekaSecim:
            case -1:
                print("İşbirlik")
            case 0:
                print("İşbirlik")
            case 1:
                print("kazık")
            case 2:
                print("kazık")
        if yapayZekaSecim == 0 or -1:  # işbirliği
                if secim.lower() == "kazık":
                    puan += 3
                    yapayZekaPuan -= 1
                else:
                    puan += 2
                    yapayZekaPuan += 2
        else:  # kazık
            if secim.lower() == "kazık":
                puan += 0          
                yapayZekaPuan += 0
            else:
                puan -= 1
                yapayZekaPuan += 3
        if secim.lower()=="kazık":
            yapayZekaSecim=random.randint(0,2)
        else:
            yapayZekaSecim=random.randint(-1,1)

    time.sleep(1)
    print("Senin puanın: ",puan)
    print("Rakibin puanı: ", yapayZekaPuan)
    if yapayZekaPuan > puan:
        print("Rakip yendi.")
    elif puan > yapayZekaPuan:
        print("Sen yendin. ")
    else:
        print("Berabere")


elif rakipSecim.lower()=="karakter":
    karakterSecim=input("Hangi karakter (Kopyacı, Çakal, Ponçik, Gözükara, Sinsi veya Rasgele karakter)?: ")
    if karakterSecim.lower()=="kopyacı":
        yapayZekaSecim = 1          # YZ ilk elde işbirliği yapsın
        oncekiHamle = None          # Senin bir önceki hamleni tutmak için #none: yok

        for game in range(10):
            secim = input("Kazık/İşbirliği: ")

            # --- KOPYACI MANTIĞI: YZ = SENİN BİR ÖNCEKİ HAMLEN ---
            if oncekiHamle is None:         # 1. elde önceki hamle yok -> varsayılan işbirliği
                yapayZekaSecim = 1
            else:
                if oncekiHamle.lower() == "kazık":
                    yapayZekaSecim = 0      # önceki elde kazık attıysan, o da şimdi kazık atar
                else:
                    yapayZekaSecim = 1      # önceki elde işbirliği yaptıysan, o da şimdi işbirliği yapar

            # --- YZ'nin hamlesini yazdır ---
            match yapayZekaSecim:
                case 1:
                    print("işbirlik")
                case 0:
                    print("Kazık")

            # --- PUANLAMA SENİN KODUN AYNISI ---
            if yapayZekaSecim == 1:  # işbirliği
                if secim.lower() == "kazık":
                    puan += 3
                    yapayZekaPuan -= 1
                else:
                    puan += 2
                    yapayZekaPuan += 2
            else:  # kazık
                if secim.lower() == "kazık":
                    puan += 0
                    yapayZekaPuan += 0
                else:
                    puan -= 1
                    yapayZekaPuan += 3

            # --- BU ELDEN SONRA: SENİN HAMLENİ SONRAKİ EL İÇİN KAYDET ---
            oncekiHamle = secim

        time.sleep(1)
        print("Senin puanın: ",puan)
        print("Rakibin puanı: ", yapayZekaPuan)
        if yapayZekaPuan > puan:
            print("Rakip yendi.")
        elif puan > yapayZekaPuan:
            print("Sen yendin. ")
        else:
            print("Berabere")

    elif karakterSecim.lower()=="çakal":
        for game in range(10):
            secim = input("Kazık/İşbirliği: ")
            print("Kazık")
            if secim.lower()=="kazık":
                puan+=0
                yapayZekaPuan+=0
            else:
                puan-=1
                yapayZekaPuan+=3
        time.sleep(1)
        print("Senin puanın: ",puan)
        print("Rakibin puanı: ", yapayZekaPuan)
        if yapayZekaPuan > puan:
            print("Rakip yendi.")
        elif puan > yapayZekaPuan:
            print("Sen yendin. ")
        else:
            print("Berabere")

    elif karakterSecim.lower()=="ponçik":
        for game in range(10):
            secim = input("Kazık/İşbirliği: ")
            print("İşbirlik")
            if secim.lower()=="kazık":
                puan+=3
                yapayZekaPuan-=1
            else:
                puan-=0
                yapayZekaPuan+=0
        time.sleep(1)
        print("Senin puanın: ",puan)
        print("Rakibin puanı: ", yapayZekaPuan)
        if yapayZekaPuan > puan:
            print("Rakip yendi.")
        elif puan > yapayZekaPuan:
            print("Sen yendin. ")
        else:
            print("Berabere")



    elif karakterSecim.lower()=="gözükara":
        kazikGorduMu = False   # henüz senden kazık görmedi

        for game in range(10):
            secim = input("Kazık/İşbirliği: ")

            # --- YZ STRATEJİSİ ---
            if kazikGorduMu:       # bir kere bile kazık gördüyse
                yapayZekaSecim = 0 # artık hep kazık
            else:
                yapayZekaSecim = 1 # şu ana kadar kazık görmediyse işbirliği

            # --- YZ'nin hamlesini yazdır ---
            match yapayZekaSecim:
                case 1:
                    print("Rakip: İşbirliği")
                case 0:
                    print("Rakip: Kazık")

            # --- PUANLAMA SENDEKİ İLE AYNI ---
            if yapayZekaSecim == 1:  # işbirliği
                if secim.lower() == "kazık":
                    puan += 3
                    yapayZekaPuan -= 1
                else:
                    puan += 2
                    yapayZekaPuan += 2
            else:  # kazık
                if secim.lower() == "kazık":
                    puan += 0
                    yapayZekaPuan += 0
                else:
                    puan -= 1
                    yapayZekaPuan += 3

            # --- OYUNCU BU TUR KAZIK ATTIYSA BİR DAHA UNUTMA ---
            if secim.lower() == "kazık":
                kazikGorduMu = True

        time.sleep(1)
        print("Senin puanın: ", puan)
        print("Rakibin puanı: ", yapayZekaPuan)
        if yapayZekaPuan > puan:
            print("Rakip yendi.")
        elif puan > yapayZekaPuan:
            print("Sen yendin. ")
        else:
            print("Berabere")
    elif karakterSecim.lower()=="sinsi":
        for game in range(10):
            match yapayZekaSecim:
                case 1:
                    print("Rakip: İşbirliği")
                case 0:
                    print("Rakip: Kazık")
            if game==3:
                yapayZekaSecim="kazık"
            else:
                yapayZekaSecim="işbirlik"
            secim=input("Kazık/İşbirliği: ")
            if secim.lower()=="kazık":
                if yapayZekaSecim==0:
                    puan+=0
                    yapayZekaPuan+=0
                else:
                    puan+=3
                    yapayZekaPuan-=1
            else:
                
