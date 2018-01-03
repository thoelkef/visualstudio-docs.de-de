---
title: "Visual Studio-Tools für Unity: Sicherheit – Exemplarische Vorgehensweise für Azure | Microsoft-Dokumentation"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: F4FD6E1C-EA64-4613-BDDE-6E4E5CCF983E
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 1ffb0c57329a8453208978cee69daa771d8ee0e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="update-unity-mono-security-certificate-store"></a>Aktualisieren des Unity Mono-Sicherheitszertifikatspeichers

Unity Mono wird mit einem leeren Zertifikatspeicher geliefert und behandelt daher sämtliche Websites als nicht vertrauenswürdig. Weitere Informationen dazu finden Sie unter [Mono security FAQ (Häufig gestellte Fragen zur Sicherheit mit Mono)](http://www.mono-project.com/docs/faq/security/).

Der Zertifikatspeicher für Unity Mono muss aktualisiert werden, damit eine Verbindung mit Azure hergestellt werden kann, ohne dabei TLS/SSL zu ignorieren.

## <a name="using-mozroots-to-install-certificates"></a>Verwenden von Mozroots zum Installieren von Zertifikaten

Das Mozroots-Tool ist in Mono enthalten. Über dieses Tool werden Stammzertifikate heruntergeladen und installiert.

1. Öffnen Sie das Eingabeaufforderungsterminal.

2. Navigieren Sie in dem Terminal zu dem Verzeichnis **C:\Programme\Unity\Editor\Data\MonoBleedingEdge\bin>**. Der genau Speicherort ist davon abhängig, wo Sie Unity auf Ihrem lokalen Computer installiert haben.

3. Geben Sie den folgenden Befehl ein, und drücken Sie dann die **EINGABETASTE**, um diesen auszuführen:

  `mono ..\lib\mono\4.5\mozroots.exe --sync --import`

4. Dabei sollten Sie die folgende Ausgabe erhalten (obwohl sich die Anzahl oder die hinzugefügten Zertifikate möglicherweise unterscheiden):

  ```
  Downloading from 'https://hg.mozilla.org/releases/mozilla-release/raw-file/default/security/nss/lib/ckfw/builtins/certdata.txt'...
  Importing certificates into user store...
  1 new root certificates were added to your trust store.
  Import process completed.
  ```

5. Jetzt sollten Sie das Beispielprojekt ausführen können, ohne Fehler zu erhalten, die im Zusammenhang mit TLS stehen.

## <a name="next-step"></a>Nächster Schritt

* [Test the client connection (Testen der Clientverbindung)](visual-studio-tools-for-unity-azure-connection.md)
