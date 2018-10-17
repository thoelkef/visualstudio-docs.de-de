---
title: Systemanforderungen für den Visual Studio-Emulator für Android | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35e766ad-269f-41e4-ba23-74a556c315f3
caps.latest.revision: 7
ms.author: crdun
manager: crdun
ms.openlocfilehash: 819f64b9d526cc307f0f9fbd0a35db5d4e7bd1ab
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176565"
---
# <a name="system-requirements-for-the-visual-studio-emulator-for-android"></a>System requirements for the Visual Studio Emulator for Android
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Der Visual Studio Emulator für Android wird in Hyper-V als virtueller Computer ausgeführt, die Virtualisierungstechnologie für Windows 8 und höhere Versionen. Um den Emulator ausführen, muss der Computer die in diesem Thema beschriebenen Voraussetzungen zum Ausführen von Hyper-V erfüllen.  
  
 Das Setup-Programm versucht bei der Installation des Emulators, diese Voraussetzungen für Sie automatisch zu konfigurieren. Wenn das Setup die Voraussetzungen erfolgreich konfiguriert hat, funktioniert der Emulator wie erwartet. Andernfalls müssen Sie diese erforderlichen Komponenten möglicherweise manuell aktivieren. Wenn Sie die erforderlichen Komponenten manuell konfigurieren müssen, entsprechen die Schritte und Tools den [hier](https://msdn.microsoft.com/library/windows/apps/jj863509\(v=vs.105\).aspx) für den Windows Phone Emulator beschriebenen Schritten.  
  
> [!IMPORTANT]
>  Das Setup-Programm für den Emulator überprüft die Voraussetzungen zum Ausführen von Visual Studio-Emulator für Android. Es zeigt Warnungen an, wenn die erforderlichen Komponenten nicht vorhanden sind, es benötigt sie jedoch nicht.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
-   [Kurze Checkliste](#Checklist)  
  
-   [Systemanforderungen](#System)  
  
-   [Netzwerkanforderungen](#Network)  
  
-   [Hyper-V-Anforderungen](#HyperV)  
  
-   [Das Ausführen des Emulators von einer startbaren virtuellen Festplatte wird nicht unterstützt](#BootableVHD)  
  
-   [Hyper-V benötigt nicht komprimierte und nicht verschlüsselte Dateien](#Files)  
  
##  <a name="Checklist"></a> Kurze Checkliste  
 Es folgt eine kurze Checkliste zu den Anforderungen zum Ausführen des Visual Studio-Emulators für Android. Ausführlichere Informationen finden Sie in den nachfolgenden Abschnitten in diesem Thema.  
  
 Systemanforderungen  
  
-   Unterstützung für Hyper-V (siehe nachstehende Anforderungen für Hyper-V)  
  
-   6 GB RAM oder mehr.  
  
-   64-Bit-Version der Pro-Edition von Windows 8, Windows 8.1, Windows 10 oder höher.  
  
-   Prozessor, der SSSE3 oder höher unterstützt.  
  
 Netzwerkanforderungen  
  
-   DHCP  
  
-   Automatisch konfigurierte DNS- und Gateway-Einstellungen  
  
 Hyper-V-Anforderungen  
  
-   Das BIOS muss folgende Funktionen unterstützen:  
  
    -   Hardwareunterstützte Virtualisierung  
  
    -   SLAT (Second Level Address Translation)  
  
    -   Datenausführungsverhinderung (DEP, Data Execution Prevention)  
  
-   Unter Windows muss Hyper-V aktiviert ist und ausgeführt werden.  
  
-   Sie müssen ein Mitglied der lokalen Administratorengruppe von Hyper-V sein.  
  
##  <a name="System"></a> Systemanforderungen  
 Ihr Computer muss die folgenden Anforderungen erfüllen:  
  
-   Hyper-V-Unterstützung (siehe [Hyper-V-Anforderungen](#HyperV))  
  
-   6 GB RAM oder mehr.  
  
-   64-Bit-Version der Pro-Edition von Windows 8, Windows 8.1, Windows 10 oder höher.  
  
 Zum Überprüfen der Anforderungen an RAM und Windows wählen Sie in der Systemsteuerung die System- und Sicherheitseinstellungen, und anschließend System.  
  
 ![Überprüfung der Systemanforderungen](../cross-platform/media/android-emu-system-requirements.png "Android_Emu_System_Requirements")  
  
##  <a name="Network"></a> Netzwerkanforderungen  
 Ihr Netzwerk muss folgende Anforderungen erfüllen:  
  
-   DHCP  
  
     Der Emulator benötigt DHCP, da er sich selbst als separates Gerät im Netzwerk mit eigener IP-Adresse konfiguriert.  
  
-   Automatisch konfigurierte DNS- und Gateway-Einstellungen  
  
     Es ist nicht möglich, die DNS und Gateway-Einstellungen für den Emulator manuell zu konfigurieren.  
  
 Informationen zum Beheben von Netzwerkproblemen im Emulator finden Sie unter den folgenden Themen:  
  
-   [Troubleshooting the Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)  
  
##  <a name="HyperV"></a> Hyper-V-Anforderungen  
 Hyper-V-Anforderungen im BIOS  
  
 Das BIOS des Computers muss folgende Anforderungen unterstützen, und muss aktiviert sein:  
  
-   Hardwareunterstützte Virtualisierung  
  
-   SLAT (Second Level Address Translation)  
  
-   Datenausführungsverhinderung (DEP, Data Execution Prevention)  
  
 Hyper-V-Anforderungen in Windows  
  
 Wenn Ihr Computer und die BIOS-Einstellungen bereits zur Unterstützung von Hyper-V konfiguriert sind, wird das Setupprogramm aktiviert und Hyper-V gestartet. Andernfalls müssen Sie diese Voraussetzungen möglicherweise manuell aktivieren.  
  
|Anforderung|Überprüfen und Aktivieren dieser Anforderung|  
|-----------------|----------------------------------------------|  
|Hyper-V muss installiert sein|Befolgen Sie dieselben Anweisungen wie zum [Aktivieren von Hyper-V für den Windows Phone Emulator](https://msdn.microsoft.com/library/windows/apps/jj863509\(v=vs.105\).aspx).<br /><br /> Überprüfen des Status des **Hyper-V-Verwaltung für virtuelle Computer** -Diensts im Dienste-Snap-In.|  
|Hyper-V muss ausgeführt werden|Weitere Informationen zum Verwalten von Diensten finden Sie unter den folgenden Themen:<br /><br /> -   [Starten, Beenden, Anhalten, Fortsetzen oder Neustarten eines Diensts](https://technet.microsoft.com/library/cc736564\(v=WS.10\).aspx)<br />-   [Konfigurieren der Startmethode für einen Dienst](https://technet.microsoft.com/%20library/cc739213\(v=ws.10\))|  
  
 Sie müssen ein Mitglied der lokalen Administratorengruppe von Hyper-V sein.  
  
 Führen Sie den Visual Studio-Emulator für Android ohne wiederholte Aufforderung zum Erhöhen Ihrer Rechte, Sie sollten Mitglied der lokalen Administratorengruppe von Hyper-V sein, aus. Wenn Sie bei der Installation des SDK bereits lokaler Administrator auf dem Computer, fügt das Setupprogramm für das SDK Sie der Gruppe der Hyper-V-Administratoren hinzu. Andernfalls müssen Sie diese Voraussetzungen möglicherweise manuell aktivieren.  
  
 Wenn Sie den Emulator ausführen, und noch kein Mitglied der Gruppe der Hyper-V-Administratoren sind, werden Sie aufgefordert, Der Gruppe beizutreten (das Dialogfeld bezieht sich auf den Windows Phone-Emulator). Für den Beitritt zu dieser Gruppe sind Administratorrechte erforderlich.  
  
> [!IMPORTANT]
> Nachdem Sie der Gruppe beigetreten sind, melden Sie sich ab und starten Sie den Computer neu, damit die Änderung wirksam wird.  
  
 ![Beitritt zur Hyper&#45;V-Administratorsicherheitsgruppe](../cross-platform/media/android-emu-hyperv-admin.png "Android_Emu_HyperV_Admin")  
  
 Um sich selbst manuell zu einer Gruppe hinzuzufügen, öffnen Sie das Snap-In für lokale Benutzer und Gruppen.
 
##  <a name="BootableVHD"></a> Das Ausführen des Emulators von einer startbaren virtuellen Festplatte wird nicht unterstützt  
 Wenn Sie versuchen, eine App im Visual Studio-Emulator für Android auszuführen, während Sie Windows von einer startbaren virtuellen Festplatte ausführen, dauert es in der Regel einige Minuten, bis der Emulator startet, oder beim Start einen Fehler ausgibt. Wenn der Emulator nicht gestartet werden kann, wird folgende Meldung angezeigt: Fehler bei der Bereitstellung der App. Versuchen Sie es erneut.  
  
 Diese Konfiguration wird nicht unterstützt. Informationen zu verwandten Problemen finden Sie unter [Troubleshooting the Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).  
  
##  <a name="Files"></a> Hyper-V benötigt nicht komprimierte und nicht verschlüsselte Dateien  
 Auf einer mit dem NTFS-Dateisystem konfigurierten Festplatte müssen die virtuellen Festplattendateien, die von Hyper-V verwendet werden, dekomprimiert und entschlüsselt werden. Stellen Sie sicher, dass die folgenden Verzeichnisse nicht komprimiert oder verschlüsselt werden:  
  
-   %localappdata%\Microsoft\XDE  
  
-   C:\Program Files (x86)\Microsoft Emulator Manager  
  
-   C:\Program Files (x86)\Microsoft Visual Studio Emulator for Android  
  
-   %localappdata%\Microsoft\VisualStudioEmulator  
  
 Im Dateisystem ReFS darf bei den virtuellen Festplattendateien nicht das Integritätsbit festgelegt sein.  
  
## <a name="hardware-graphics-forwarding-opengl-es-support-requirements"></a>Hardwareanforderungen für das Weiterleiten von Grafiken (OpenGL ES-Unterstützung)  
 Damit der Emulator Aufrufe an die GPU simulieren kann, wie z. B. von OpenGL-ES, muss Ihr Computer eine DirectX-kompatible GPU besitzen und die entsprechenden DirectX-Treiber müssen installiert sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehlerbehebung beim Visual Studio-Emulator für Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)

