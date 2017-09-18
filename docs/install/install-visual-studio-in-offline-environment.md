---
title: Besonderheiten bei der Installation von Visual Studio in einer Offlineumgebung | Microsoft-Dokumentation
description: '{{PLATZHALTER}}'
ms.date: 06/05/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: 1ce2f854d1c8e4a184446fb07c66a6fad9ca9ae1
ms.contentlocale: de-de
ms.lasthandoff: 06/23/2017

---
# <a name="special-considerations-for-installing-visual-studio-in-an-offline-environment"></a>Besonderheiten bei der Installation von Visual Studio in einer Offlineumgebung

Visual Studio ist in erster Linie auf die Installation auf Computern mit Internetzugriff ausgelegt, da viele Komponenten regelmäßig aktualisiert werden. Mithilfe einiger zusätzlicher Schritte ist es jedoch möglich, Visual Studio in einer Umgebung bereitzustellen, in der keine funktionierende Internetverbindung vorhanden ist.

## <a name="install-certificates-needed-for-visual-studio-offline-installation"></a>Installieren der für eine Offlineinstallation von Visual Studio erforderlichen Zertifikate
Das Visual Studio-Setupprogramm installiert nur Inhalte, die als vertrauenswürdig eingestuft werden. Dies macht es, indem es Authenticode-Signaturen von Inhalten überprüft, die heruntergeladen werden, und vor deren Installation prüft, ob diese vertrauenswürdig sind. So wird Ihre Umgebung vor Angriffen geschützt, bei denen der Speicherort des Downloads kompromittiert wird. Das Setup von Visual Studio erfordert deshalb, dass mehrere Standardstamm- und Zwischenzertifikate von Microsoft auf dem Computer des Benutzers installiert und auf dem neuesten Stand sind. Wenn der Computer immer über die aktuellsten Windows Updates verfügt, werden die Signaturzertifikate immer automatisch aktualisiert. Während der Installation aktualisiert Visual Studio die Zertifikate bei Bedarf für die Überprüfung von Dateisignaturen. 

Administratoren können für Unternehmen mit Offlinecomputern, die nicht über die aktuellsten Stammzertifikate verfügen, mit [diesen Anweisungen](https://technet.microsoft.com/en-us/library/dn265983.aspx) die Aktualisierungen durchführen. Alternativ können Sie die notwendigen Zertifikate auch während des Erstellens eines Netzwerklayouts in den Ordner `certificates` herunterladen und manuell installieren, indem Sie doppelt auf die Zertifikatdatei klicken und dann dem Zertifikat-Manager-Assistenten folgen. Wenn Sie nach einem Kennwort gefragt werden, lassen Sie es leer.

Wenn Sie die Bereitstellung von Visual Studio in einer Offlineumgebung für Clientarbeitsstationen skripten, sollten Sie folgende Schritte durchführen:

1. Kopieren Sie das [Zertifikat-Manager-Tool](https://msdn.microsoft.com/en-us/library/e78byta0.aspx) (`certmgr.exe`) in die Installationsfreigabe (z.B. `\\server\share\vs2017`). `certmgr.exe` ist nicht in Windows selbst enthalten, ist aber als Teil der [Windows SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) verfügbar. 

2. Erstellen Sie eine Batchdatei mit den folgenden Befehlen:

   ```cmd
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA 2011" -s -r LocalMachine CA
   
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   
   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA 2010" -s -r LocalMachine CA
   
   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   
   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA
   
   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```

3. Stellen Sie die Batchdatei für den Client bereit. Dieser Befehl sollte in einem erhöhten Prozess ausgeführt werden.

### <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Was sind die Zertifikatdateien im `certificates`-Ordner?
Die drei `.p12`-Dateien in diesem Ordner enthalten jeweils ein Zwischen- und ein Stammzertifikat. Auf den meisten Systemen, die über die aktuellsten Windows Updates verfügen, sind diese Zertifikate bereits installiert.

1. `ManifestSignCertificates.p12` enthält:
    * Ein Zwischenzertifikat: **Microsoft Code Signing PCA 2011**
        * Nicht erforderlich Wenn Sie dieses Zertifikat haben, verbessert es die Leistung in einigen Szenarios.
    * Ein Stammzertifikat: **Microsoft Root Certificate Authority 2011**
        * Ist auf Systemen unter Windows 7 Service Pack 1 erforderlich, auf denen nicht die aktuellsten Windows Updates installiert sind
2. `ManifestCounterSignCertificates.p12`
    * Ein Zwischenzertifikat: **Microsoft Time-Stamp PCA 2010**
        * Nicht erforderlich Wenn Sie dieses Zertifikat haben, verbessert es die Leistung in einigen Szenarios.
    * Ein Stammzertifikat: **Microsoft Root Certificate Authority 2010**
        * Ist auf Systemen unter Windows 7 Service Pack 1 erforderlich, auf denen nicht die aktuellsten Windows Updates installiert sind
3. `vs_installer_opc.SignCertificates.p12`
    * Ein Zwischenzertifikat: **Microsoft Code Signing PCA**
        * Auf allen Systemen erforderlich. Beachten Sie, dass Systeme mit allen Windows Updates möglicherweise nicht über dieses Zertifikat verfügen.
    * Ein Stammzertifikat: **Microsoft Root Certificate Authority**
        * Erforderlich. Dieses Zertifikat ist in allen Systemen unter Windows 7 oder höher enthalten.

### <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Warum werden die Zertifikate aus dem Ordner `certificates` nicht automatisch installiert?
Wenn eine Signatur in einer Onlineumgebung überprüft wird, werden Windows-APIs zum Herunterladen und Hinzufügen der Zertifikate zum System verwendet. Im Verlauf dieses Vorgangs wird mithilfe administrativer Einstellungen geprüft, ob das Zertifikat vertrauenswürdig und zulässig ist. Diese Überprüfung kann in den meisten Offlineumgebungen nicht erfolgen. Durch das manuelle Installieren der Zertifikate kann der Enterprise-Administrator sicherstellen, dass die Zertifikate vertrauenswürdig sind und die Sicherheitsrichtlinien ihrer Organisation zu erfüllen.

### <a name="checking-if-certificates-are-already-installed"></a>Prüfen, ob Zertifikate bereits installiert sind
Eine Möglichkeit, das installierte System zu prüfen, sind die folgenden Schritte:
* Führen Sie „mmc.exe“ aus.
* Klicken Sie auf „Datei“ und dann auf „Add/Remove Snap-in“ (Snap-In hinzufügen/entfernen).
  * Klicken Sie doppelt auf **Zertifikate**, dann auf **Computerkonto** und anschließend auf **Weiter**.
  * Klicken Sie auf **Lokaler Computer**, dann auf **Fertig stellen** und anschließend auf **OK**.
  * Erweitern Sie **Zertifikate (Lokaler Computer)**.
  * Erweitern Sie **Vertrauenswürdige Stammzertifizierungsstellen** und klicken Sie dann auf **Zertifikate**.
    * Überprüfen Sie die Liste auf erforderliche Stammzertifikate.
  * Erweitern Sie **Zwischenzertifizierungsstellen** und klicken Sie auf **Zertifikate**.
    * Überprüfen Sie diese Liste auf erforderliche Zwischenzertifikate.
* Klicken Sie auf „Datei“ und dann auf „Add/Remove Snap-in“ (Snap-In hinzufügen/entfernen).
  * Klicken Sie doppelt auf **Zertifikate**, dann auf **Eigenes Benutzerkonto**, **Fertig stellen** und anschließend auf **OK**.
  * Erweitern Sie **Zertifikate – Aktueller Benutzer**.
  * Erweitern Sie **Zwischenzertifizierungsstellen** und klicken Sie auf **Zertifikate**.
    * Überprüfen Sie diese Liste auf erforderliche Zwischenzertifikate.
    
Wenn sich die Zertifikatnamen nicht in der Spalte **Ausgestellt für** befinden, müssen Sie installiert werden.  Wenn sich ein Zwischenzertifikat nur im Speicher des Zwischenzertifikats **Aktueller Benutzer** befindet, steht es nur für den angemeldeten Benutzer zur Verfügung und muss möglicherweise für andere Benutzer installiert werden.

## <a name="install-visual-studio"></a>Installieren von Visual Studio
Nach der Installation der Zertifikate kann die Bereitstellung von Visual Studio offline ohne zusätzliche spezielle Schritte unter Befolgung der [hier beschriebenen Anweisungen](create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation) fortgesetzt werden.


## <a name="see-also"></a>Siehe auch
* [Installieren von Visual Studio](install-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Arbeitsauslastung und Komponenten-IDs von Visual Studio](workload-and-component-ids.md)

