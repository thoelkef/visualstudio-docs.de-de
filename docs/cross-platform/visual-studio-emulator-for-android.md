---
title: "Visual Studio-Emulator für Android | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80f0104f-a4db-44dd-bd55-37bb67776c62
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 07f3e972f06707f21543b5a70c9712d9706a3980
ms.contentlocale: de-de
ms.lasthandoff: 05/13/2017

---
# <a name="visual-studio-emulator-for-android"></a>Visual Studio-Emulator für Android
Der Visual Studio-Emulator für Android ist eine Desktopanwendung, die ein Android-Gerät emuliert. Er bietet eine virtualisierte Umgebung, in der Sie Android-Apps ohne physisches Gerät debuggen und testen können. Darüber bietet er eine isolierte Umgebung für Ihre Anwendungsprototypen.  
  
 Der Visual Studio-Emulator für Android soll mit einem echten Gerät vergleichbare Leistung bereitstellen. Bevor Sie Ihre App veröffentlichen, wird jedoch empfohlen, die App auf einem physischen Gerät zu testen.  
  
 Sie können Ihre App mit einem eindeutigen Geräteprofil für jede Android-Plattform, Bildschirmauflösung und andere Hardwareeigenschaften testen, die vom Visual Studio-Emulator für Android unterstützt werden.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
-   [Installation und Deinstallation](#Installing)  
  
-   [Systemanforderungen und Abwärtskompatibilität](#Requirements)  
  
-   [Netzwerkeinbindung des Visual Studio-Emulators für Android](#Networking)  
  
-   [Konfiguration des Visual Studio-Emulators für Android](#Configuring)  
  
-   [Funktionen, die Sie im Emulator testen können](#FeaturesTest)  
  
-   [Features, die Sie im Emulator nicht testen können](#FeaturesNonTest)  
  
-   [Supportressourcen](#Support)  
  
##  <a name="Installing"></a> Installation und Deinstallation  
 Installation  
  
 Der Visual Studio-Emulator für Android ist eine Komponente der in Visual Studio verfügbaren plattformübergreifenden Tools, die während einer benutzerdefinierten Installation von Visual Studio installiert werden, wenn Sie plattformübergreifende mobile Entwicklung, allgemeine Tools und Software Development Kits und dann Visual Studio-Emulator für Android auswählen.  
  
 Deinstallieren  
  
 Sie können den Visual Studio-Emulator für Android in der Systemsteuerung mithilfe der Option „Software“ deinstallieren.  
  
> [!NOTE]
>  Beim Deinstallieren von Visual Studio wird der Emulator nicht deinstalliert. Sie müssen den Emulator separat deinstallieren.  
  
 Bei der Deinstallation des Visual Studio-Emulators für Android werden die für den Emulator erstellten virtuellen Hyper-V Ethernet-Adapter nicht automatisch entfernt. Sie können diese virtuellen Adapter (sofern sie nicht verwendet werden) manuell entfernen, indem Sie den Hyper-V-Manager öffnen und eines der VHD-Emulatorimages sowie die Registerkarte „Netzwerk“ und dann **Entfernen** für jeden auf dieser Registerkarte angezeigten Switch auswählen.  
  
##  <a name="Requirements"></a> Systemanforderungen und Abwärtskompatibilität  
 Wichtige Informationen über die Hardware, Software und Konfigurationsanforderungen für den Visual Studio-Emulator für Android finden Sie unter dem folgenden Thema.  
  
-   [System Requirements for the Visual Studio Emulator for Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
 Der Visual Studio-Emulator für Android benötigt Visual Studio 2015. Es ist nicht abwärtskompatibel mit früheren Versionen von Visual Studio.  
  
 Neue Versionen des Emulators werden über alte Versionen installiert (und können in einigen Fällen die alten Images ersetzen, auf diesen Images installierte Einstellungen, Anwendungen und Dateien verwerfen).  
  
##  <a name="Networking"></a> Netzwerkeinbindung des Visual Studio-Emulators für Android  
 Die Netzwerkverbindung des Visual Studio-Emulators für Android verhält sich wie die Verbindung von einem Desktopcomputer mit folgenden Merkmalen:  
  
-   Der Emulator wird im Netzwerk als separates Gerät mit eigener IP-Adresse angezeigt.  
  
-   Es erfordert keine zusätzliche Netzwerksoftware, die nicht bereits mit dem Emulator installiert wurde.  
  
-   Er wird nicht mit einer Windows-Domäne verknüpft.  
  
 Um die Funktionen der Netzwerkverbindung des Emulators zu verstehen, stellen Sie sie sich als Wi-Fi-Verbindung von Ihrem Android-Telefon mit dem gleichen Netzwerk vor. Wenn eine Anwendung auf Ihrem Telefon über die Wi-Fi-Verbindung auf eine Netzwerkressource zugreifen kann, dann kann eine im Emulator ausgeführte App ebenfalls auf dieselbe Netzwerkressource zugreifen.  
  
 Weitere Informationen zu den Netzwerkanforderungen finden Sie unter [Systemanforderungen für den Visual Studio-Emulator für Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
 Informationen zur Behebung von Netzwerkproblemen finden Sie unter [Fehlerbehebung beim Visual Studio-Emulator für Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).  
  
##  <a name="Configuring"></a> Konfiguration des Visual Studio-Emulators für Android  
 Das Testen Ihrer Android-App auf Kompatibilität mit der beeindruckenden Vielzahl von Android-Hardware kann eine Herausforderung darstellen. Android-Telefone und Tablet-PCs auf dem Markt umfassen eine Vielzahl von Versionen und Bildschirmgrößen und sind in zahlreichen unterschiedlichen Hardwarekonfigurationen (Arbeitsspeicher, CPUs, Architektur usw.) verfügbar. Der Visual Studio-Emulator für Android vereinfacht dieses Szenario anhand von Geräteprofilen. Unsere Geräteprofile stellen die am häufigsten verwendete Hardware auf dem Markt dar, einschließlich der Geräte von Samsung, Motorola, Sony, LG und vielen mehr.  
  
 In Visual Studio 2015 können Sie Geräteprofile mithilfe des Emulator-Managers installieren, deinstallieren und starten. Greifen Sie auf den Emulator-Manager zu, indem Sie auf **Extras**, und dann auf **Visual Studio-Emulator für Android** klicken.  
  
 ![Visual Studio-Emulator für Android-Manager](~/cross-platform/media/android_emu_manager.png "Android_Emu_Manager")  
  
 In der Standardeinstellung sind vier vorinstallierte Geräteprofile verfügbar (KitKat und Lollipop Phone/5 "und Tablet/7"-Konfigurationen), wie durch weißen Text und Symbole gekennzeichnet. Andere Profile in der Liste werden abgeblendet, bis Sie auf die Schaltfläche **Profil installieren** klicken und die Installation abgeschlossen ist. Sie können die Liste nach API-Ebene filtern und auf den Details-Pfeil unten rechts in einem Profil klicken, um die vollständigen Konfigurationsdetails anzuzeigen.  
  
 Nachdem Sie die Profile installiert haben, die Sie als Ziel verwenden möchten, können Sie diese neuen Profile direkt aus dem Manager starten, indem Sie auf die grüne Schaltfläche **Abspielen** klicken. Sie werden auch im Dropdownmenü Debug-Ziel in einem plattformübergreifenden mobilen Projekttyp in Visual Studio angezeigt.  
  
##  <a name="FeaturesTest"></a> Funktionen, die Sie im Emulator testen können  
 Ausführliche Informationen zu Features, die Sie im Emulator testen können, finden Sie in dieser [Dokumentation](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx).  
  
##  <a name="FeaturesNonTest"></a> Features, die Sie im Emulator nicht testen können  
 In der folgenden Liste sind Funktionen der Android-Plattform aufgeführt, die Sie im Emulator **nicht** testen können. Sie müssen diese Funktionen auf einem physischen Gerät testen.  
  
-   Kompass  
  
-   Gyroskop  
  
-   Vibrationscontroller  
  
-   Helligkeit. Das Verändern der Helligkeitsstufe des Emulators hat keine visuellen Auswirkungen auf die Anzeige des Geräts auf Ihrem Bildschirm.  
  
##  <a name="Support"></a> Supportressourcen  
 Wenn Ihr Hostcomputer die Systemanforderungen erfüllt und Sie ein Problem feststellen, das in diesem Handbuch zur Problembehandlung nicht erörtert wird, müssen Sie Folgendes vornehmen:  
  
-   Stellen Sie eine Frage zu StackOverflow unter Verwendung der Tags [android-emulator](http://stackoverflow.com/questions/tagged/android-emulator) und „visual-studio“.  
  
-   Melden Sie ein Problem mithilfe des Tools „Lächeln senden“ in Visual Studio oder im Emulator-Manager.  
  
## <a name="see-also"></a>Siehe auch  
 [Systemanforderungen für den Visual Studio-Emulator für Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)   
 [Fehlerbehebung beim Visual Studio-Emulator für Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
