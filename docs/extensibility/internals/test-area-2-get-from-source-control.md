---
title: "Testbereich 2: Abrufen von Datenquellen-Steuerelement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Quellcode-Plug-ins und Abrufen von Elementen aus der Datenquellen-Steuerelement"
  - "Abrufen von Elementen aus der Datenquellen-Steuerelement [Visual Studio SDK]"
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Testbereich 2: Abrufen von Datenquellen-Steuerelement
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Test Hierunter Testfälle für das Abrufen von Elementen aus dem Versionsspeicher über den Befehl abrufen. Diese Testfälle können sowohl lokale und Webprojekte angewendet werden.  
  
## Befehl Menüzugriff  
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrated Development\-Umgebung im Menüpfade werden in den Testfällen verwendet.  
  
##### Letzte Version abrufen:  
  
-   **Datei**, **Quellcodeverwaltung**, **Letzte Version abrufen**.  
  
-   **Datei**, **Letzte Version abrufen**.  
  
-   Klicken Sie im Kontextmenü **Letzte Version abrufen**.  
  
-   Get: **Datei**, **Quellcodeverwaltung**, **abrufen**.  
  
## Es wird erwartet  
  
##### Letzte Version abrufen:  
 Führt eine automatische Installation \(keine Benutzeroberfläche\) Abrufen der neuesten Version des Elements aus dem Versionsspeicher.  
  
##### Erhalten:  
 Zeigt die **abrufen** Dialogfeld und der Benutzer zum Ändern der Dateigruppe, die abgerufen werden soll und ändern Sie die Optionen, die beeinflussen, wie die Dateien abgerufen werden kann.  
  
## Testfälle  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|------------------|-------------------------------------|  
|Erhalten Sie die neueste Version der Datei, die nicht lokal vorhanden ist|1.  Erstellen eines Projekts.<br />2.  Fügen Sie dem Projekt ein Element.<br />3.  Fügen Sie das Projekt unter Versionskontrolle.<br />4.  Löschen Sie die lokale Kopie des Elements.<br />5.  Abrufen der neuesten Version des Elements \(klicken Sie im Kontextmenü **Letzte Version abrufen**\).|Elementdatei wird lokal abgerufen.|  
|Abrufen einer Datei, die nicht lokal vorhanden ist|1.  Erstellen eines Projekts.<br />2.  Fügen Sie dem Projekt ein Element.<br />3.  Fügen Sie das Projekt unter Versionskontrolle.<br />4.  Löschen Sie die lokale Kopie des Elements.<br />5.  Abrufen des Elements \(**Datei**, **Quellcodeverwaltung**, **abrufen** \< Element \>\).|Elementdatei wird lokal abgerufen.|  
|Abrufen einer Datei, die exklusiv ausgecheckt und lokal geändert wurden|1.  Erstellen eines Projekts.<br />2.  Fügen Sie dem Projekt ein Element.<br />3.  Fügen Sie das Projekt unter Versionskontrolle.<br />4.  Checken Sie ausschließlich das Projektelement.<br />5.  Ändern Sie die lokale Kopie.<br />6.  Abrufen der neuesten Version des Elements \(**Datei**, **Letzte Version abrufen, der** \< Element \>\). Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächstem Schritt.<br />7.  Klicken Sie auf **Ersetzen** Schaltfläche im Dialogfeld "Warnung".|**In Schritt 6 reResult** `:`<br /><br /> Im Dialogfeld Warnung gibt an, dass die Datei ausgecheckt ist.<br /><br /> **ReResult aus Schritt 7:**<br /><br /> Geänderte lokale Datei wird von der ursprünglichen Version aus dem Versionsspeicher ersetzt.<br /><br /> Datei ist Lese\-\/Schreibzugriff.|  
|Abrufen Sie und Ersetzen Sie die Datei, die ausgecheckt wird, freigegeben und lokal geändert|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie dem Projekt ein Element.<br />3.  Fügen Sie das Projekt unter Versionskontrolle.<br />4.  Sehen Sie sich das Projektelement als freigegeben.<br />5.  Ändern Sie die lokale Kopie.<br />6.  Abrufen der neuesten Version des Elements \(**Datei**, **Letzte Version abrufen, der** \< Element \>\). Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächstem Schritt.<br />7.  Klicken Sie auf **Ersetzen** im Dialogfeld "Warnung".|**Führen Sie in Schritt 6:**<br /><br /> Im Dialogfeld Warnung gibt an, dass die Datei ausgecheckt ist.<br /><br /> **Führen Sie in Schritt 7:**<br /><br /> Geänderte lokale Datei wird von der ursprünglichen Version aus dem Versionsspeicher ersetzt.<br /><br /> Datei ist Lese\-\/Schreibzugriff.|  
|Erhalten Sie eine Datei, die lokal vorhanden ist wie die neueste Version im Versionsspeicher|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie dem Projekt ein Element.<br />3.  Fügen Sie das Projekt unter Versionskontrolle.<br />4.  Abrufen des Elements \(**Datei**, **Quellcodeverwaltung**, **abrufen** \< Element \>\).|Lokaler Datei bleibt unverändert.|  
|Eine Lösung mit einem Projekt|1.  Erstellen Sie eine Projektmappe mit einem Projekt.<br />2.  Platzieren Sie die Projektmappe unter Versionskontrolle.<br />3.  Löschen Sie alle Projektdateien lokal.<br />4.  Abrufen der Lösung \(**Datei**, **Quellcodeverwaltung**, **abrufen**\).|Alle gelöschten Dateien werden lokal wiederhergestellt.|  
  
## Siehe auch  
 [Test\-Handbuch für Source Control\-Plug\-ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)