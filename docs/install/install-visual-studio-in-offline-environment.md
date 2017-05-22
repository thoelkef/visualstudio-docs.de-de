---
title: Besonderheiten bei der Installation von Visual Studio in einer Offlineumgebung | Microsoft-Dokumentation
description: '{{PLATZHALTER}}'
ms.date: 05/09/2017
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
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: b596b6b6f9cff58525d253157534b6b990c68fcd
ms.contentlocale: de-de
ms.lasthandoff: 05/09/2017

---
# <a name="special-considerations-for-installing-visual-studio-in-an-offline-environment"></a>Besonderheiten bei der Installation von Visual Studio in einer Offlineumgebung

Visual Studio ist in erster Linie auf die Installation auf Computern mit Internetzugriff ausgelegt, da viele Komponenten regelmäßig aktualisiert werden. Mithilfe einiger zusätzlicher Schritte ist es jedoch möglich, Visual Studio in einer Umgebung bereitzustellen, in der keine funktionierende Internetverbindung vorhanden ist.

## <a name="create-a-network-installation-layout"></a>Erstellen eines Layouts für die Netzwerkinstallation
* Details finden Sie unter [Erstellen einer netzwerkbasierten Installation von Visual Studio](create-a-network-installation-of-visual-studio.md).

## <a name="install-certificates-needed-for-visual-studio-offline-installation"></a>Installieren der für eine Offlineinstallation von Visual Studio erforderlichen Zertifikate
Das Visual Studio-Setupprogramm installiert nur Inhalte, die als vertrauenswürdig eingestuft werden.  Es überprüft Authenticode-Signaturen von Inhalten, die heruntergeladen werden, und prüft vor ihrer Installation, ob diese vertrauenswürdig sind.  Computer mit Internetzugriff laden erforderliche Zertifikate automatisch herunterladen und installieren sie, um Dateisignaturen zu überprüfen.  Doch wenn Sie in einer Offlineumgebung oder auf einem System mit schlechter Internetverbindung arbeiten, ist dies ggf. nicht möglich.  Für Benutzer in dieser Umgebung müssen Sie sicherstellen, dass die erforderlichen Zertifikate vorinstalliert sind.  Diese Zertifikate werden vom ausführenden Computer in den Ordner „Zertifikate“ heruntergeladen, wenn eine Offlineinstallation erstellt wird.

Sie können die Zertifikate auf dem Client installieren, indem Sie manuell auf die Zertifikatdatei doppelklicken und anschließend den Zertifikat-Manager-Assistenten durchlaufen. Wenn Sie nach einem Kennwort gefragt werden, lassen Sie es leer.

Um ein Skript für die Installation der Zertifikate zu erstellen, gehen Sie folgendermaßen vor:

1. Kopieren Sie „certmgr.exe“ in die Installationsfreigabe (z. B. `\server\share\vs2017`). `certmgr.exe` ist im Lieferumfang des Windows SDK enthalten, das als optionale Komponente in der Workload _Entwicklung für die universelle Windows-Plattform_ installiert werden kann. (Beispiel: `"C:\Program Files (x86)\Windows Kits\10\bin\x86\certmgr.exe"`)

2. Erstellen Sie eine Batchdatei mit den folgenden Befehlen:

```cmd
\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
```

3. Führen Sie die Batchdatei auf dem Client in einer Administratorbefehlsshell oder in einem Prozess mit erhöhten Rechten aus.

### <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Warum werden die Zertifikate aus dem Ordner `certificates` nicht automatisch installiert?
Wenn eine Signatur in einer Onlineumgebung überprüft wird, werden Windows-APIs zum Herunterladen und Hinzufügen der Zertifikate zum System verwendet. Im Verlauf dieses Vorgangs wird mithilfe administrativer Einstellungen geprüft, ob das Zertifikat vertrauenswürdig und zulässig ist. Diese Überprüfung kann in den meisten Offlineumgebungen nicht erfolgen. Das manuelle Installieren der Zertifikate ermöglicht dem Benutzer das Sicherstellen, dass die Zertifikate vertrauenswürdig sind und die Administratoranforderungen erfüllen.

## <a name="install-visual-studio"></a>Installieren von Visual Studio
Nach der Installation der Zertifikate kann die Bereitstellung von Visual Studio offline ohne zusätzliche spezielle Schritte unter Befolgung der [hier beschriebenen Anweisungen](create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation) fortgesetzt werden.


## <a name="see-also"></a>Siehe auch
* [Installieren von Visual Studio](install-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Arbeitsauslastung und Komponenten-IDs von Visual Studio](workload-and-component-ids.md)

