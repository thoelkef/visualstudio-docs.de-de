---
title: 'Testbereich 2: Abrufen aus der Quellcodeverwaltung | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a9ec7071a1e4ca78bb116c577cdcc77f9798c050
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="test-area-2-get-from-source-control"></a>Testbereich 2: Abrufen von Datenquellen-Steuerelements
Dieser Testbereich werden die Testfälle zum Abrufen von Elementen aus dem Versionsspeicher über den Befehl Get behandelt. Diese Testfälle können sowohl lokale Pipes und Webprojekte angewendet werden.  
  
## <a name="command-menu-access"></a>Menüzugriff Befehl  
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrated Development-Umgebung im Menüpfade werden in den Testfällen verwendet.  
  
##### <a name="get-latest-version"></a>Letzte Version abrufen:  
  
-   **Datei**, **Quellcodeverwaltung**, **letzte Version abrufen**.  
  
-   **Datei**, **letzte Version abrufen**.  
  
-   Klicken Sie im Kontextmenü **neuste Version abrufen**.  
  
-   Get: **Datei**, **Quellcodeverwaltung**, **abrufen**.  
  
## <a name="expected-behavior"></a>Erwartetes Verhalten  
  
##### <a name="get-latest-version"></a>Letzte Version abrufen:  
 Führt eine automatische (ohne Benutzeroberfläche) Abrufen der neuesten Version des Elements aus dem Versionsspeicher.  
  
##### <a name="get"></a>Erhalten:  
 Zeigt die **abrufen** (Dialogfeld), und ermöglicht dem Benutzer die Datei ändern, die abgerufen werden soll sowie zum Ändern der Optionen, die beeinflussen, wie die Dateien abgerufen werden.  
  
## <a name="test-cases"></a>Testfälle  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Abrufen der neuesten Version der Datei, die nicht lokal vorhanden ist|1.  Erstellen eines Projekts.<br />2.  Fügen Sie dem Projekt ein Element hinzu.<br />3.  Fügen Sie das Projekt unter quellcodeverwaltung.<br />4.  Löschen Sie die lokale Kopie des Elements.<br />5.  Abrufen der neuesten Version des Elements (klicken Sie im Kontextmenü **neuste Version abrufen**).|Elementdatei wird lokal abgerufen.|  
|Abrufen einer Datei, die nicht lokal vorhanden ist|1.  Erstellen eines Projekts.<br />2.  Fügen Sie dem Projekt ein Element hinzu.<br />3.  Fügen Sie das Projekt unter quellcodeverwaltung.<br />4.  Löschen Sie die lokale Kopie des Elements.<br />5.  Abrufen des Elements (**Datei**, **Quellcodeverwaltung**, **abrufen** \<Item >).|Elementdatei wird lokal abgerufen.|  
|Abrufen einer Datei, die exklusiv ausgecheckt und lokal geändert wurde|1.  Erstellen eines Projekts.<br />2.  Fügen Sie dem Projekt ein Element hinzu.<br />3.  Fügen Sie das Projekt unter quellcodeverwaltung.<br />4.  Checken Sie das Projektelement ausschließlich aus.<br />5.  Ändern Sie die lokale Kopie.<br />6.  Abrufen der neuesten Version des Elements (**Datei**, **neuste Version abrufen, der** \<Item >). Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächsten Schritt fort.<br />7.  Klicken Sie auf **ersetzen** Schaltfläche im Dialogfeld "Warnung".|**In Schritt 6 reResult**`:`<br /><br /> Warnungsdialogfeld gibt an, dass die Datei ausgecheckt ist.<br /><br /> **ReResult aus Schritt 7:**<br /><br /> Geänderte lokale Datei wird durch die ursprüngliche Version aus dem Versionsspeicher ersetzt.<br /><br /> Datei ist Lese-/Schreibzugriff.|  
|Abrufen Sie und Ersetzen Sie die Datei, die ausgecheckt, freigegebene und lokal geändert|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie dem Projekt ein Element hinzu.<br />3.  Fügen Sie das Projekt unter quellcodeverwaltung.<br />4.  Sehen Sie sich das Projektelement als freigegebener.<br />5.  Ändern Sie die lokale Kopie.<br />6.  Abrufen der neuesten Version des Elements (**Datei**, **neuste Version abrufen, der** \<Item >). Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächsten Schritt fort.<br />7.  Klicken Sie auf **ersetzen** im Dialogfeld "Warnung".|**Führen Sie in Schritt 6:**<br /><br /> Warnungsdialogfeld gibt an, dass die Datei ausgecheckt ist.<br /><br /> **Führen Sie in Schritt 7:**<br /><br /> Geänderte lokale Datei wird durch die ursprüngliche Version aus dem Versionsspeicher ersetzt.<br /><br /> Datei ist Lese-/Schreibzugriff.|  
|Abrufen einer Datei, die lokal vorhanden ist identisch mit der neuesten Version im Versionsspeicher|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie dem Projekt ein Element hinzu.<br />3.  Fügen Sie das Projekt unter quellcodeverwaltung.<br />4.  Abrufen des Elements (**Datei**, **Quellcodeverwaltung**, **abrufen** \<Item >).|Lokale Datei wird nicht geändert.|  
|Erhalten Sie eine Projektmappe mit einem Projekt|1.  Erstellen Sie eine Projektmappe mit einem Projekt ein.<br />2.  Platzieren Sie die Projektmappe unter quellcodeverwaltung.<br />3.  Löschen Sie alle Projektdateien lokal.<br />4.  Abrufen die Projektmappe (**Datei**, **Quellcodeverwaltung**, **abrufen**).|Alle gelöschten Dateien werden lokal wiederhergestellt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)