---
title: "Testbereich 5: Change-Datenquellen-Steuerelement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ändern der Datenquellen-Steuerelement [Visual Studio SDK]"
  - "Source Control-Plug-ins Ändern von Datenquellen-Steuerelement"
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Testbereich 5: Change-Datenquellen-Steuerelement
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Datenquellen\-Steuerelement Test\-Plug\-in Hierunter ändern das Datenquellen\-Steuerelement über die **Quellcodeverwaltung ändern** Befehl.  
  
 **Quellcodeverwaltung ändern** Befehl bietet vier grundlegende Funktionen für den Benutzer:  
  
-   **Binden:**  
  
     Ermöglicht einem Benutzer oder Wiederherstellen einer Source Control Verknüpfung zwischen einer Projektmappe oder eines Projekts und des Versionsspeichers.  
  
-   **Aufheben der Bindung:**  
  
     Entfernt eine Projektmappe aus Datenquellen\-Steuerelement auf einer Basis pro Verbindung.  
  
-   **Anschließen und trennen:**  
  
 Schaltet\-verbunden oder offline\-Status der kontrollierten Lösung, die im Bereich 3 behandelt wird. Weitere Informationen finden Sie unter [Testbereich 3: Auschecken \/ Auschecken rückgängig machen](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).  
  
## Befehl Menüzugriff  
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrated Development\-Umgebung im Menüpfad wird in den Testfällen verwendet.  
  
 Quellcodeverwaltung ändern:**Datei**, **Quellcodeverwaltung**, **Datenquellen\-Steuerelement ändern**.  
  
## Testfälle  
 Im folgenden sind bestimmte Testfälle für die **Quellcodeverwaltung ändern** Befehl Testbereich.  
  
### Fall 5a: Binden  
 Bindung kann der Benutzer Informationen zur Quelle Code Steuerelement ausgewählte Projekte und Projektmappen hinzufügen. In der Regel wird der Benutzer aufgefordert, ein Projekt im Datenquellen\-Steuerelement bezeichnet, werden diese hinzugefügt werden. Der Benutzer kann ein neues Projekt nicht im Datenquellen\-Steuerelement als Teil dieses Vorgangs \(Kontrast mit zur Quellcodeverwaltung hinzufügen\) erstellen.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|------------------|-------------------------------------|  
|Binden an leerer Speicherort|1.  Erstellen eines Projekts.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Öffnen Sie **Quellcodeverwaltung ändern** \(Dialogfeld\) \(**Datei**, **Source Control**, **Quellcodeverwaltung ändern**\).<br />4.  Klicken Sie auf **Bindung**.<br />5.  Im Dialogfeld Warnung wird akzeptiert, wenn es angezeigt wird.<br />6.  Alle Elemente auswählen.<br />7.  Klicken Sie auf **binden**.<br />8.  Navigieren Sie zu eine leere Stelle in einem Datenquellen\-Steuerelement gespeichert.<br />9. Klicken Sie auf **OK** schließen die **Quellcodeverwaltung ändern** \(Dialogfeld\).<br />10. Klicken Sie auf **Bindungsvorgang fortsetzen** im Dialogfeld zur Bestätigung.<br />11. Klicken Sie auf **OK** im Dialogfeld Warnung, wenn es angezeigt wird.<br />12. Alles einchecken. Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächstem Schritt.<br />13. Öffnen Sie die Projektmappe aus Datenquellen\-Steuerelement an eine neue Position.|`Result from Step 12:`<br /><br /> Projektmappen\- und Projektdateien werden an und zum neuen Ziel im Versionsspeicher geschrieben.<br /><br /> Projektmappen\-und Projektdateien werden überprüft.<br /><br /> Version Store Projekthierarchie entspricht die Ordnerstruktur des Projekts auf dem Datenträger.<br /><br /> `Result from Step 13:`<br /><br /> Alle Projektelemente werden heruntergeladen.|  
|Binden Sie an den Speicherort, mit dem Client synchronisiert werden|1.  Erstellen eines Projekts.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Erstellen Sie ein Duplikat der Projektmappe und Projekt im Versionsspeicher \(freigeben und Verzweigen, wenn [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]\).<br />4.  Öffnen Sie **Quellcodeverwaltung ändern** \(Dialogfeld\) \(**Datei**, **Source Control**, **Quellcodeverwaltung ändern**\).<br />5.  Lösen Sie alle heraus.<br />6.  Klicken Sie auf **OK** schließen **Quellcodeverwaltung ändern** \(Dialogfeld\).<br />7.  Öffnen Sie erneut **Quellcodeverwaltung ändern** \(Dialogfeld\).<br />8.  Wählen Sie alle.<br />9. Klicken Sie auf **binden**.<br />10. Navigieren Sie zum verzweigte Speicherort der Projektmappe und Projekt \(aus Schritt 3\)<br />11. Klicken Sie auf **OK** schließen die **Quellcodeverwaltung ändern** \(Dialogfeld\).<br />12. Rufen Sie aktuelle rekursiv für alle Elemente.|Inhalt der Datei nach dem Abrufen wird derselbe ist wie vor dem abrufen.|  
|Binden Sie an, die nicht mit dem Client synchronisiert wird|1.  Erstellen eines Projekts.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Erstellen Sie ein Duplikat der Projektmappe und Projekt im Versionsspeicher \(freigeben und Verzweigen, wenn [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]\).<br />4.  Ändern Sie verzweigte Projektdateien im Versionsspeicher.<br />5.  Öffnen Sie **Quellcodeverwaltung ändern** \(Dialogfeld\) \(**Datei**, **Source Control**, **Quellcodeverwaltung ändern**\).<br />6.  Lösen Sie alle heraus.<br />7.  Klicken Sie auf **OK** schließen **Quellcodeverwaltung ändern** \(Dialogfeld\).<br />8.  Öffnen Sie erneut **Quellcodeverwaltung ändern** \(Dialogfeld\).<br />9. Wählen Sie alle.<br />10. Klicken Sie auf **binden**.<br />11. Navigieren Sie zum Speicherort für die Projektmappe und das Projekt verzweigt.<br />12. Klicken Sie auf **OK** schließen die **Quellcodeverwaltung ändern** \(Dialogfeld\).<br />13. Im Dialogfeld Warnung wird akzeptiert, wenn es angezeigt wird.<br />14. Erhalten Sie aktuelle rekursiv für alle Elemente.|Dateien, die in Schritt 4 geändert wurden, werden auch lokal geändert.|  
|Binden Sie die Lösung, die nie in einem Quellcodeverwaltungsprojekt wurde|1.  Erstellen Sie einen leeren Ordner im Datenquellen\-Steuerelement.<br />2.  Erstellen Sie ein Clientprojekt.<br />3.  Öffnen Sie **Quellcodeverwaltung ändern** \(Dialogfeld\) \(**Datei**, **Source Control**, **Quellcodeverwaltung ändern**\).<br />4.  Binden Sie die Projektmappe an leere Stelle im Datenquellen\-Steuerelement.<br />5.  Klicken Sie auf **OK** schließen die **Quellcodeverwaltung ändern** \(Dialogfeld\).<br />6.  Klicken Sie auf **Bindungsvorgang fortsetzen** im Dialogfeld zur Bestätigung.<br />7.  Klicken Sie auf **OK** im Dialogfeld Warnung, wenn es angezeigt wird.|Datenquellen\-Steuerelement wird der Projektmappe hinzugefügt.<br /><br /> Projektmappen\- und Projektdateien werden ausgecheckt.|  
|Cancel\-Bindung|1.  Erstellen eines Projekts.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Öffnen Sie das Dialogfeld Datenquellen\-Steuerelement ändern.<br />4.  Lösen Sie alle heraus.<br />5.  Klicken Sie auf **OK** um das Dialogfeld zu schließen. Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächstem Schritt.<br />6.  Öffnen Sie erneut die **Quellcodeverwaltung ändern** \(Dialogfeld\).<br />7.  Binden Sie an unabhängigen Speicherort.<br />8.  Klicken Sie auf **Abbrechen**.|`Result from Step 5:`<br /><br /> Die Lösung ist nicht mehr in der quellcodeverwaltung<br /><br /> `Result from Step 8:`<br /><br /> Lösung ist nicht im Datenquellen\-Steuerelement.|  
  
### Fall 5: Aufheben der Bindung  
 Aufheben der Bindung entfernt Code Steuerelement Quellinformationen aus Projekten und deren Lösung. Die betroffenen Projekte und Projektmappen basieren auf einer Mischung Benutzerauswahl und wie die Elemente zur Versionskontrolle hinzugefügt wurden.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|------------------|-------------------------------------|  
|Aufheben der Bindung Projektmappe, die ein Dateisystem oder lokalen IIS\-Webprojekt und eine Client\-Projekt enthält.|1.  Erstellen Sie ein Dateisystem oder lokalen IIS\-Webprojekt.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Fügen Sie eine neue Client\-Projekt zur Projektmappe hinzu.<br />4.  Überprüfen der Lösung akzeptieren Sie, wenn Sie aufgefordert werden.<br />5.  Öffnen Sie die **Quellcodeverwaltung ändern** \(Dialogfeld\).<br />6.  Klicken Sie auf **Bindung**.<br />7.  Klicken Sie auf **OK** um das Dialogfeld zu schließen.<br />8.  So checken Sie die Projektmappe "," Projekt "," Projektmappenelemente "," Projektelemente versuchen.|Projektmappen und Projekte sind nicht verwaltet.<br /><br /> Source Control Menübefehle werden nicht angezeigt.|  
|Aufheben der Bindung Abbrechen|1.  Erstellen eines Projekts.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Öffnen Sie die **Quellcodeverwaltung ändern** \(Dialogfeld\).<br />4.  Klicken Sie auf **loszulösen alle**.<br />5.  Klicken Sie auf **Abbrechen**.|Lösung besteht in der quellcodeverwaltung.|  
  
### Fall 5c: erneut binden  
 Binden ist einfach eine Kombination von Unbind und Binden – der Prozess das erneute Binden einer Projekt\/Projektmappe, die zuvor unter Versionskontrolle und war ungebundenen.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|------------------|-------------------------------------|  
|Binden von Projektmappen und Projekten, ohne dass dazu die **Quellcodeverwaltung ändern** \(Dialogfeld\)|1.  Erstellen eines Projekts.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Öffnen Sie die **Quellcodeverwaltung ändern** \(Dialogfeld\).<br />4.  Klicken Sie auf **Bindung**.<br />5.  Wählen Sie alle Zeilen.<br />6.  Klicken Sie auf **binden**.<br />7.  Klicken Sie auf **OK** schließen die **Quellcodeverwaltung ändern** \(Dialogfeld\).<br />8.  Akzeptieren Sie auschecken, wenn Sie aufgefordert werden.|Projektmappen\- und Projektdateien werden unter dem Datenquellen\-Steuerelement.|  
|Nur ohne schließende Projekt binden **Quellcodeverwaltung ändern** \(Dialogfeld\)|1.  Erstellen eines Projekts.<br />2.  Fügen Sie nur das Projekt mit Source Control \(Datei \-\> Source Control \-\> ausgewählte Projekte zur Quellcodeverwaltung hinzufügen.<br />3.  Öffnen Sie das Dialogfeld Datenquellen\-Steuerelement ändern.<br />4.  Aufheben der Bindung nur des Projekts.<br />5.  Binden Sie nur das Projekt.|Die Lösung ist nicht gesteuerten.<br /><br /> Projekt bleibt kontrolliert.|  
|Binden Sie die Projektmappe nur ohne schließende **Quellcodeverwaltung ändern** \(Dialogfeld\)|1.  Erstellen eines Projekts.<br />2.  Fügen Sie nur die Lösung mit Source Control \(**Datei**, **Quellcodeverwaltung**, **Ausgewählte Projekte zur Quellcodeverwaltung hinzufügen**.<br />3.  Öffnen Sie die **Quellcodeverwaltung ändern** \(Dialogfeld\).<br />4.  Aufheben der Bindung nur der Lösung \(lassen Sie **Quellcodeverwaltung ändern** Dialogfeld.\)<br />5.  Binden Sie nur die Lösung.<br />6.  Klicken Sie auf **OK**, um das Dialogfeld zu schließen.<br />7.  Auschecken von Projektmappen und Projektmappenelemente \(sofern vorhanden.\)|Die Lösung ist kontrolliert.<br /><br /> Projekt bleibt unkontrollierten.|  
|Binden Sie die Projektmappe oder eines Projekts nur, wenn es sich im selben Verzeichnis|1.  Erstellen eines Projekts.<br />2.  Fügen Sie nur das Projekt mit Source Control \(**Datei**, **Quellcodeverwaltung**, **Ausgewählte Projekte zur Quellcodeverwaltung hinzufügen**.<br />3.  Schließen Sie die Projektmappe.<br />4.  Erstellen Sie eine neue Projektmappe mit mindestens zwei Projekte.<br />5.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />6.  Fügen Sie das Projekt, das in Schritt 1 aus Datenquellen\-Steuerelement erstellt.<br />7.  Akzeptieren Sie das Auschecken der Lösung, wenn Sie aufgefordert werden.<br />8.  Überprüfen Sie in der gesamten Lösung.<br />9. Öffnen Sie die **Quellcodeverwaltung ändern** \(Dialogfeld\).<br />10. Wählen Sie das hinzugefügte Projekt \(aus Schritt 6\), und klicken Sie auf **Unbind**.<br />11. Klicken Sie auf **OK**, um das Dialogfeld zu schließen.<br />12. Übernehmen Sie das Auschecken, wenn Sie aufgefordert werden.<br />13. Öffnen Sie erneut **Quellcodeverwaltung ändern** \(Dialogfeld\).<br />14. Wählen Sie das hinzugefügte Projekt \(aus Schritt 6\), und klicken Sie auf **binden**.<br />15. Wählen Sie den ursprünglichen Speicherort.|Projektmappen und Projekte bleiben kontrolliert.|  
  
## Siehe auch  
 [Test\-Handbuch für Source Control\-Plug\-ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)