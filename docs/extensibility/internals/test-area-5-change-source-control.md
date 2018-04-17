---
title: 'Testbereich 5: Ändern der Quellcodeverwaltung | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e7fd014bf520ee2f0515e284f2fb5430961cd407
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="test-area-5-change-source-control"></a>Testbereich 5: Change-Datenquellen-Steuerelements
Dieser Bereich der quellcodeverwaltung für die Test-Plug-in behandelt, ändern die quellcodeverwaltung über das **Quellcodeverwaltung ändern** Befehl.  
  
 **Ändern Sie die Datenquellen-Steuerelements** Befehl bietet vier grundlegende Funktionen für den Benutzer:  
  
-   **Binden:**  
  
     Ermöglicht es einem Benutzer hergestellt oder eine Quelle Steuerelement-Verknüpfung zwischen einer Projektmappe/Projekt und den Versionsspeicher wiederherzustellen.  
  
-   **Aufheben der Bindung:**  
  
     Entfernt eine Projektmappe aus der quellcodeverwaltung pro Verbindung.  
  
-   **Eine Verbindung herstellen/trennen:**  
  
 Schaltet-verbunden oder offline-Status des gesteuerten Projektmappe, die im Bereich 3 abgedeckt wird. Weitere Informationen finden Sie unter [Test Bereich 3: Auschecken / rückgängig: Auschecken](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).  
  
## <a name="command-menu-access"></a>Menüzugriff Befehl  
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrated Development-Umgebung im Menüpfad wird in den Testfällen verwendet.  
  
 Quellcodeverwaltung ändern:**Datei**, **Quellcodeverwaltung**, **Quellcodeverwaltung ändern**.  
  
## <a name="test-cases"></a>Testfälle  
 Im folgenden sind bestimmte Testfälle für die **Quellcodeverwaltung ändern** Befehl Testbereich angezeigt.  
  
### <a name="case-5a-bind"></a>Fall 5a: Binden  
 Bindung kann der Benutzer ausgewählte Projekte und Projektmappen Source Code Control Informationen hinzugefügt. In der Regel wird der Benutzer aufgefordert, ein Projekt in der quellcodeverwaltung identifizieren, dem diese hinzugefügt werden. Der Benutzer kann ein neues Projekt in der quellcodeverwaltung im Rahmen dieses Vorgangs (Gegensatz zur Quellcodeverwaltung hinzufügen) nicht erstellt werden.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Binden an leerer Speicherort|1.  Erstellen eines Projekts.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Open **Quellcodeverwaltung ändern** (Dialogfeld) (**Datei**, **Quellcodeverwaltung**, **Quellcodeverwaltung ändern**).<br />4.  Klicken Sie auf **Bindung**.<br />5.  Akzeptieren Sie Warndialogfeld, sofern sie angezeigt wird.<br />6.  Wählen Sie alle Elemente an.<br />7.  Klicken Sie auf **binden**.<br />8.  Navigieren Sie zum leerer Speicherort in einem Speicher der quellcodeverwaltung.<br />9. Klicken Sie auf **OK** schließen die **Quellcodeverwaltung ändern** (Dialogfeld).<br />10. Klicken Sie auf **Bindungsvorgang fortsetzen** im Bestätigungsdialogfeld angezeigt wurde.<br />11. Klicken Sie auf **OK** im Warndialogfeld, sofern sie angezeigt wird.<br />12. Checken Sie alles. Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächsten Schritt fort.<br />13. Öffnen Sie Projektmappen aus der quellcodeverwaltung an einem neuen Speicherort.|`Result from Step 12:`<br /><br /> Projektmappen- und Projektdateien werden an gebunden und in das neue Ziel im Versionsspeicher geschrieben.<br /><br /> Projektmappen-und Projektdateien werden eingecheckt.<br /><br /> Version Store Projekthierarchie entspricht der Ordnerhierarchie des Projekts auf dem Datenträger.<br /><br /> `Result from Step 13:`<br /><br /> Alle Projektelemente werden heruntergeladen.|  
|Binden Sie an den Speicherort, der mit dem Client synchronisiert wurde|1.  Erstellen eines Projekts.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Erstellen Sie ein Duplikat der Projektmappen- und Projektdateien im Versionsspeicher (freigeben und Verzweigen, wenn mit [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />4.  Open **Quellcodeverwaltung ändern** (Dialogfeld) (**Datei**, **Quellcodeverwaltung**, **Quellcodeverwaltung ändern**).<br />5.  Aufheben der Bindung alle.<br />6.  Klicken Sie auf **OK** schließen **Quellcodeverwaltung ändern** (Dialogfeld).<br />7.  Öffnen Sie erneut **Quellcodeverwaltung ändern** (Dialogfeld).<br />8.  Alles auswählen.<br />9. Klicken Sie auf **binden**.<br />10. Navigieren Sie zum verzweigten Speicherort der Projektmappe und Projekt (aus Schritt 3)<br />11. Klicken Sie auf **OK** schließen die **Quellcodeverwaltung ändern** (Dialogfeld).<br />12. Rufen Sie aktuelle rekursiv für alle Elemente.|Dateiinhalt nach Get ist derselbe ist wie vor dem abrufen.|  
|Binden Sie an den Speicherort, der nicht mit dem Client synchron|1.  Erstellen eines Projekts.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Erstellen Sie ein Duplikat der Projektmappen- und Projektdateien im Versionsspeicher (freigeben und Verzweigen, wenn mit [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />4.  Ändern Sie die Dateien im Projekt verzweigten im Versionsspeicher.<br />5.  Open **Quellcodeverwaltung ändern** (Dialogfeld) (**Datei**, **Quellcodeverwaltung**, **Quellcodeverwaltung ändern**).<br />6.  Aufheben der Bindung alle.<br />7.  Klicken Sie auf **OK** schließen **Quellcodeverwaltung ändern** (Dialogfeld).<br />8.  Öffnen Sie erneut **Quellcodeverwaltung ändern** (Dialogfeld).<br />9. Alles auswählen.<br />10. Klicken Sie auf **binden**.<br />11. Navigieren Sie zum Speicherort für Projektmappe und Projekt verzweigt.<br />12. Klicken Sie auf **OK** schließen die **Quellcodeverwaltung ändern** (Dialogfeld).<br />13. Akzeptieren Sie Warndialogfeld, sofern sie angezeigt wird.<br />14, Abgerufen Sie neueste rekursiv für alle Elemente werden.|Dateien, die in Schritt 4 geändert wurden, werden auch lokal geändert.|  
|Binden Sie die Projektmappe, die nie in der quellcodeverwaltung wurde|1.  Erstellen Sie einen leeren Ordner, in der quellcodeverwaltung.<br />2.  Erstellen Sie ein Clientprojekt.<br />3.  Open **Quellcodeverwaltung ändern** (Dialogfeld) (**Datei**, **Quellcodeverwaltung**, **Quellcodeverwaltung ändern**).<br />4.  Binden Sie die Projektmappe an leerer Speicherort in der quellcodeverwaltung an.<br />5.  Klicken Sie auf **OK** schließen die **Quellcodeverwaltung ändern** (Dialogfeld).<br />6.  Klicken Sie auf **Bindungsvorgang fortsetzen** im Bestätigungsdialogfeld angezeigt wurde.<br />7.  Klicken Sie auf **OK** im Warndialogfeld, sofern sie angezeigt wird.|Datenquellen-Steuerelement wird der Projektmappe hinzugefügt.<br /><br /> Projektmappen- und Projektdateien werden ausgecheckt.|  
|Cancel-Bindung|1.  Erstellen eines Projekts.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Öffnen Sie das Dialogfeld der Quellcodeverwaltung ändern.<br />4.  Aufheben der Bindung alle.<br />5.  Klicken Sie auf **OK** Schaltfläche, um das Dialogfeld zu schließen. Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächsten Schritt fort.<br />6.  Öffnen Sie erneut die **Quellcodeverwaltung ändern** (Dialogfeld).<br />7.  Binden Sie an nicht verknüpfte Speicherort.<br />8.  Klicken Sie auf **"Abbrechen"**.|`Result from Step 5:`<br /><br /> Die Lösung ist nicht mehr in der quellcodeverwaltung<br /><br /> `Result from Step 8:`<br /><br /> Lösung ist noch nicht unter quellcodeverwaltung.|  
  
### <a name="case-5b-unbind"></a>Fall 5 b: Aufheben der Bindung  
 Heben Sie die Bindung entfernt Code Steuerelement Quellinformationen aus Projekten und deren Lösung. Die betroffenen Projekte und Projektmappen basieren auf einer Kombination aus Benutzerauswahl und wie die Elemente zur quellcodeverwaltung hinzugefügt wurden.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Heben Sie die Projektmappe mit einem Dateisystem oder lokalen IIS-Webprojekt und ein Clientprojekt Bindung|1.  Erstellen Sie ein Dateisystem oder lokalen IIS-Webprojekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Ein neues Clientprojekt zur Projektmappe hinzufügen.<br />4.  Überprüfen der Lösung akzeptieren Sie, wenn Sie aufgefordert werden.<br />5.  Öffnen der **Quellcodeverwaltung ändern** (Dialogfeld).<br />6.  Klicken Sie auf **Bindung**.<br />7.  Klicken Sie auf **OK**, um das Dialogfeld zu schließen.<br />8.  Versucht, die Projektmappe "," Projekt "," Projektmappenelemente "," Projektelemente Auschecken.|Projektmappen und Projekte sind nicht in der quellcodeverwaltung.<br /><br /> Befehle im Menü zur Quelle werden nicht angezeigt.|  
|Heben Sie die Bindung "Abbrechen"|1.  Erstellen eines Projekts.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Öffnen der **Quellcodeverwaltung ändern** (Dialogfeld).<br />4.  Klicken Sie auf **Bindung alle**.<br />5.  Klicken Sie auf **"Abbrechen"**.|Lösung besteht in der quellcodeverwaltung.|  
  
### <a name="case-5c-rebind"></a>Case-5c: erneut binden  
 Seitenindex ist einfach eine Kombination von Unbind und Bind – der Prozess das erneute Binden einer Projekt/Projektmappe, die zuvor in der quellcodeverwaltung und wurde aufgehoben.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Binden von Projektmappen und Projekten ohne schließende der **Quellcodeverwaltung ändern** (Dialogfeld)|1.  Erstellen eines Projekts.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Öffnen der **Quellcodeverwaltung ändern** (Dialogfeld).<br />4.  Klicken Sie auf **Bindung**.<br />5.  Wählen Sie alle Zeilen.<br />6.  Klicken Sie auf **binden**.<br />7.  Klicken Sie auf **OK** schließen die **Quellcodeverwaltung ändern** (Dialogfeld).<br />8.  Akzeptieren Sie auschecken, wenn Sie aufgefordert werden.|Projektmappen- und Projektdateien sind in der quellcodeverwaltung.|  
|Binden des Projekts nur ohne schließende **Quellcodeverwaltung ändern** (Dialogfeld)|1.  Erstellen eines Projekts.<br />2.  Fügen Sie nur das Projekt mit Source Control (File-Source Control -> ausgewählte Projekte zur Quellcodeverwaltung hinzufügen.<br />3.  Öffnen Sie das Dialogfeld der Quellcodeverwaltung ändern.<br />4.  Heben Sie die Bindung nur des Projekts.<br />5.  Binden Sie nur das Projekt.|Lösung bleibt nicht gesteuert.<br /><br /> Projekt bleibt gesteuerte.|  
|Binden Sie die Projektmappe nur ohne schließende **Quellcodeverwaltung ändern** (Dialogfeld)|1.  Erstellen eines Projekts.<br />2.  Fügen Sie nur die Lösung mit Source Control (**Datei**, **Quellcodeverwaltung**, **ausgewählte Projekte zur Quellcodeverwaltung hinzufügen**.<br />3.  Öffnen der **Quellcodeverwaltung ändern** (Dialogfeld).<br />4.  Heben Sie die Bindung nur auf der Projektmappe (Schließen nicht **Quellcodeverwaltung ändern** (Dialogfeld).)<br />5.  Nur die Lösung zu binden.<br />6.  Klicken Sie auf **OK**, um das Dialogfeld zu schließen.<br />7.  Sehen Sie sich die Projektmappe und Projektmappenelemente, (falls vorhanden)|Lösung bleibt gesteuerte.<br /><br /> Projekt bleibt nicht gesteuert.|  
|Binden Sie die Projektmappe/Projekt nur, wenn es sich im gleichen Verzeichnis ab|1.  Erstellen eines Projekts.<br />2.  Fügen Sie nur das Projekt mit Source Control (**Datei**, **Quellcodeverwaltung**, **ausgewählte Projekte zur Quellcodeverwaltung hinzufügen**.<br />3.  Schließen Sie die Projektmappe.<br />4.  Erstellen Sie eine neue Projektmappe mit mindestens zwei Projekte.<br />5.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />6.  Fügen Sie das Projekt, das in Schritt 1 erstellt haben, aus der quellcodeverwaltung hinzu.<br />7.  Akzeptieren Sie das Auschecken der Lösung, wenn Sie aufgefordert werden.<br />8.  Überprüfen Sie in der gesamten Projektmappe.<br />9. Öffnen der **Quellcodeverwaltung ändern** (Dialogfeld).<br />10. Wählen Sie die hinzugefügte Projekt (aus Schritt 6), und klicken Sie auf **Unbind**.<br />11. Klicken Sie auf **OK**, um das Dialogfeld zu schließen.<br />12. Akzeptieren Sie das Auschecken rückgängig, wenn Sie aufgefordert werden.<br />13. Öffnen Sie erneut **Quellcodeverwaltung ändern** (Dialogfeld).<br />14, Wählen Sie die hinzugefügte Projekt (aus Schritt 6), und klicken Sie auf **binden**.<br />15. Wählen Sie den ursprünglichen Speicherort.|Projektmappen und Projekte bleiben gesteuerte.|  
  
## <a name="see-also"></a>Siehe auch  
 [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)