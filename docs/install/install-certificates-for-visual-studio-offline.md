---
title: Installieren der für eine Offlineinstallation von Visual Studio erforderlichen Zertifikate | Microsoft-Dokumentation
description: Beschreibt die erforderlichen Schritte für die Installation von Zertifikaten für eine Offlineinstallation von Visual Studio
ms.date: 08/30/2017
ms.reviewer: tims
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: tglee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 548e00743381e6a2c39d87d82c587b26f944702a
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2018
---
# <a name="install-certificates-required-for-visual-studio-offline-installation"></a>Installieren der für eine Offlineinstallation von Visual Studio erforderlichen Zertifikate

Visual Studio ist in erster Linie auf die Installation auf Computern mit Internetzugriff ausgelegt, da viele Komponenten regelmäßig aktualisiert werden. Mithilfe einiger zusätzlicher Schritte ist es jedoch möglich, Visual Studio in einer Umgebung bereitzustellen, in der keine funktionierende Internetverbindung vorhanden ist.

Das Visual Studio-Setupprogramm installiert nur Inhalte, die als vertrauenswürdig eingestuft werden. Dies macht es, indem es Authenticode-Signaturen von Inhalten überprüft, die heruntergeladen werden, und vor deren Installation prüft, ob diese vertrauenswürdig sind. So wird Ihre Umgebung vor Angriffen geschützt, bei denen der Speicherort des Downloads kompromittiert wird. Das Setup von Visual Studio erfordert deshalb, dass mehrere Standardstamm- und Zwischenzertifikate von Microsoft auf dem Computer des Benutzers installiert und auf dem neuesten Stand sind. Wenn der Computer mit Windows Update auf dem neuesten Stand gehalten wird, sind die Signaturzertifikate in der Regel auf dem neuesten Stand. Wenn der Computer mit dem Internet verbunden ist, werden die Zertifikate während der Installation von Visual Studio bei Bedarf möglicherweise erneuert, um Dateisignaturen zu aktualisieren. Wenn der Computer offline ist, müssen die Zertifikate auf eine andere Art aktualisiert werden.

## <a name="how-to-refresh-certificates-when-offline"></a>Aktualisieren von Zertifikaten im Offlinemodus

Es gibt drei Optionen, Zertifikate in einer Offlineumgebung zu installieren oder zu aktualisieren.

### <a name="option-1---manually-install-certificates-from-a-layout-folder"></a>Option 1: Manuelles Installieren von Zertifikaten aus einem Layoutordner

Wenn Sie ein Netzwerklayout erstellen, werden die erforderlichen Zertifikate in den Ordner „Zertifikate“ heruntergeladen. Sie können die Zertifikate manuell installieren, indem Sie auf die Zertifikatdateien doppelklicken und anschließend den Zertifikat-Manager-Assistenten durchlaufen. Wenn Sie nach einem Kennwort gefragt werden, lassen Sie es leer.

### <a name="option-2---distribute-trusted-root-certificates-in-an-enterprise-environment"></a>Option 2: Verteilen von vertrauenswürdigen Stammzertifikaten in einer Unternehmensumgebung

Administratoren können für Unternehmen mit Offlinecomputern, die nicht über die aktuellsten Stammzertifikate verfügen, mit den Anweisungen auf der seite [Konfigurieren vertrauenswürdiger Stämme und unzulässiger Zertifikate](https://technet.microsoft.com/library/dn265983.aspx) die Aktualisierungen durchführen.

### <a name="option-3---install-certificates-as-part-of-a-scripted-deployment-of-visual-studio"></a>Option 3: Installieren von Zertifikaten als Teil einer skriptgesteuerten Bereitstellung von Visual Studio

Wenn Sie die Bereitstellung von Visual Studio in einer Offlineumgebung für Clientarbeitsstationen skripten, sollten Sie folgende Schritte durchführen:

1. Kopieren Sie das [Zertifikat-Manager-Tool](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) in die Installationsfreigabe (z.B. \\server\share\vs2017). Certmgr.exe ist nicht in Windows selbst enthalten, ist aber als Teil der [Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) verfügbar.

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

## <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Was sind die Zertifikatdateien im Ordner „Zertifikate“?

Die drei P12-Dateien in diesem Ordner enthalten jeweils ein Zwischen- und ein Stammzertifikat. Auf den meisten Systemen, die über die aktuellsten Windows-Updates verfügen, sind diese Zertifikate bereits installiert.

* **ManifestSignCertificates.p12** enthält:
    * Ein Zwischenzertifikat: **Microsoft Code Signing PCA 2011**
        * Nicht erforderlich Wenn Sie dieses Zertifikat haben, verbessert es die Leistung in einigen Szenarios.
    * Ein Stammzertifikat: **Microsoft Root Certificate Authority 2011**
        * Ist auf Systemen unter Windows 7 Service Pack 1 erforderlich, auf denen nicht die aktuellsten Windows Updates installiert sind
* **ManifestCounterSignCertificates.p12** enthält:
    * Ein Zwischenzertifikat: **Microsoft Time-Stamp PCA 2010**
        * Nicht erforderlich Wenn Sie dieses Zertifikat haben, verbessert es die Leistung in einigen Szenarios.
    * Ein Stammzertifikat: **Microsoft Root Certificate Authority 2010**
        * Ist auf Systemen unter Windows 7 Service Pack 1 erforderlich, auf denen nicht die aktuellsten Windows Updates installiert sind
* **Vs_installer_opc.SignCertificates.p12** enthält:
    * Ein Zwischenzertifikat: **Microsoft Code Signing PCA**
        * Auf allen Systemen erforderlich. Beachten Sie, dass Systeme mit allen Windows-Updates möglicherweise nicht über dieses Zertifikat verfügen.
    * Ein Stammzertifikat: **Microsoft Root Certificate Authority**
        * Erforderlich. Dieses Zertifikat ist in allen Systemen unter Windows 7 oder höher enthalten.

## <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Warum werden die Zertifikate aus dem Ordner „Zertifikate“ nicht automatisch installiert?

Wenn eine Signatur in einer Onlineumgebung überprüft wird, werden Windows-APIs zum Herunterladen und Hinzufügen der Zertifikate zum System verwendet. Im Verlauf dieses Vorgangs wird mithilfe administrativer Einstellungen geprüft, ob das Zertifikat vertrauenswürdig und zulässig ist. Diese Überprüfung kann in den meisten Offlineumgebungen nicht erfolgen. Durch das manuelle Installieren der Zertifikate kann der Enterprise-Administrator sicherstellen, dass die Zertifikate vertrauenswürdig sind und die Sicherheitsrichtlinien ihrer Organisation zu erfüllen.

## <a name="checking-if-certificates-are-already-installed"></a>Prüfen, ob Zertifikate bereits installiert sind

Eine Möglichkeit, das installierte System zu prüfen, sind die folgenden Schritte:
1. Führen Sie **mmc.exe** aus.<br/>
  a. Klicken Sie auf „Datei“ und dann auf **Snap-In hinzufügen/entfernen**.<br/>
  b. Doppelklicken Sie auf **Zertifikate**, dann auf **Computerkonto** und anschließend auf **Weiter**.<br/>
  c. Klicken Sie auf **Lokaler Computer**, dann auf **Fertig stellen** und anschließend auf **OK**.<br/>
  d. Erweitern Sie **Zertifikate (Lokaler Computer)**.<br/>
  e. Erweitern Sie **Vertrauenswürdige Stammzertifizierungsstellen**, und klicken Sie dann auf **Zertifikate**.<br/>
    * Überprüfen Sie die Liste auf erforderliche Stammzertifikate.<br/>

   f. Erweitern Sie **Zwischenzertifizierungsstellen**, und klicken Sie auf **Zertifikate**.<br/>
    * Überprüfen Sie diese Liste auf erforderliche Zwischenzertifikate.<br/>

2. Klicken Sie auf „Datei“ und dann auf **Snap-In hinzufügen/entfernen**.<br/>
  a. Doppelklicken Sie auf **Zertifikate**, dann auf **Eigenes Benutzerkonto**, **Fertig stellen** und anschließend auf **OK**.<br/>
  b. Erweitern Sie **Zertifikate – Aktueller Benutzer**.<br/>
  c. Erweitern Sie **Zwischenzertifizierungsstellen**, und klicken Sie auf **Zertifikate**.<br/>
    * Überprüfen Sie diese Liste auf erforderliche Zwischenzertifikate.<br/>

Wenn sich die Zertifikatnamen nicht in der Spalte **Ausgestellt für** befinden, müssen Sie installiert werden.  Wenn sich ein Zwischenzertifikat nur im Speicher des Zwischenzertifikats **Aktueller Benutzer** befindet, steht es nur für den angemeldeten Benutzer zur Verfügung. Sie sollten es für andere Benutzer herunterladen.

## <a name="install-visual-studio"></a>Installieren von Visual Studio

Nach der Installation der Zertifikate kann die Bereitstellung von Visual Studio mithilfe der Anweisungen aus dem Abschnitt [Bereitstellen über eine Netzwerkinstallation](create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation) der Seite „Erstellen einer Netzwerkinstallation von Visual Studio“ fortgesetzt werden.

## <a name="get-support"></a>Support aufrufen
Manchmal kann etwas schiefgehen. Wenn bei der Installation von Visual Studio ein Fehler auftritt, lesen Sie den Artikel [Problembehandlung bei Visual Studio 2017-Installations- und -Upgradefehlern](troubleshooting-installation-issues.md). Wenn keiner der Schritte zur Problembehandlung hilfreich ist, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://www.visualstudio.com/vs/support/#talktous).

Hier sind einige weitere Supportoptionen:
* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Sie können uns einen Produktvorschlag unter [UserVoice](https://visualstudio.uservoice.com/forums/121579) mitteilen.
* Sie können Probleme mit Produkten im Portal [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) im Blick behalten, Fragen stellen und Antworten finden.
* Über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) können Sie auch Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufnehmen.  (Diese Option erfordert ein [GitHub](https://github.com/)-Konto.)

## <a name="see-also"></a>Siehe auch
* [Installieren von Visual Studio](install-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Arbeitsauslastung und Komponenten-IDs von Visual Studio](workload-and-component-ids.md)
