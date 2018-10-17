---
title: 'Testbereich 5: Ändern der Quellcodeverwaltung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 808ed1ce13af06fa263a339bc9c6788595a261a6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229254"
---
# <a name="test-area-5-change-source-control"></a>Testbereich 5: Ändern der Quellcodeverwaltung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quellcodeverwaltung-Plug-in Test Hierunter ändern die Datenquellen-Steuerelement über die **Quellcodeverwaltung ändern** Befehl.  
  
 **Ändern Sie die Quellcodeverwaltung** Befehl bietet vier grundlegende Funktionen für den Benutzer:  
  
-   **Binden:**  
  
     Ermöglicht einem Benutzer zum Herstellen oder zum Wiederherstellen einer Datenquellen-Steuerelement-Verknüpfung zwischen einer Projektmappe oder eines Projekts und den Versionsspeicher.  
  
-   **Aufheben der Bindung:**  
  
     Entfernt eine Projekt/Projektmappe aus der quellcodeverwaltung auf einer Basis pro Verbindung.  
  
-   **Verbindung herstellen/trennen:**  
  
 Schaltet-Online- oder offline-Status der kontrollierte Lösung, die im Bereich 3 beschrieben wird. Weitere Informationen finden Sie unter [Test Bereich 3: Auschecken / Auschecken rückgängig machen](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).  
  
## <a name="command-menu-access"></a>Menüzugriff Befehl  
 Die folgenden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrierte Development-Umgebung im Menüpfad wird verwendet, in den Testfällen.  
  
 Quellcodeverwaltung ändern:**Datei**, **Quellcodeverwaltung**, **ändern, Datenquellen-Steuerelement**.  
  
## <a name="test-cases"></a>Testfälle  
 Im folgenden sind bestimmte Testfälle für die **Quellcodeverwaltung ändern** Befehl Testbereich.  
  
### <a name="case-5a-bind"></a>Case-5a: Binden  
 Bindung kann der Benutzer ausgewählte Projekte und Projektmappen Source Code Control Informationen hinzugefügt. In der Regel wird der Benutzer aufgefordert, ein Projekt in der quellcodeverwaltung identifizieren, der diese hinzugefügt werden. Der Benutzer kann ein neues Projekt in der quellcodeverwaltung im Rahmen dieses Vorgangs (Kontrast zur Quellcodeverwaltung hinzufügen) nicht erstellt werden.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Binden an leerer Speicherort|1.  Erstellen eines Projekts.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Open **Quellcodeverwaltung ändern** (Dialogfeld) (**Datei**, **Quellcodeverwaltung**, **Quellcodeverwaltung ändern**).<br />4.  Klicken Sie auf **Aufheben der Bindung**.<br />5.  Akzeptieren Sie Sie im Dialogfeld Warnung, wenn er angezeigt wird.<br />6.  Alle Elemente auswählen.<br />7.  Klicken Sie auf **binden**.<br />8.  Navigieren Sie zu der eine leere Position in einem Speicher der quellcodeverwaltung.<br />9. Klicken Sie auf **OK** schließen die **Quellcodeverwaltung ändern** Dialogfeld.<br />10. Klicken Sie auf **Bindungsvorgang fortsetzen** im Dialogfeld zur Bestätigung.<br />11. Klicken Sie auf **OK** in das Warnungsdialogfeld, wenn es angezeigt wird.<br />12. Alles einchecken. Wenn dieser Schritt erfolgreich ist, können Sie mit nächsten Schritt fort.<br />13. Öffnen Sie Projektmappe aus der quellcodeverwaltung an einem neuen Speicherort.|`Result from Step 12:`<br /><br /> Projektmappen- und Projektdateien werden an gebunden und in das neue Ziel im Versionsspeicher geschrieben.<br /><br /> Projektmappen-und Projektdateien werden eingecheckt.<br /><br /> Version Store Projekthierarchie entspricht die Ordnerstruktur des Projekts auf dem Datenträger.<br /><br /> `Result from Step 13:`<br /><br /> Alle Projektelemente werden heruntergeladen.|  
|Binden Sie an den Speicherort, der mit dem Client synchronisiert wird|1.  Erstellen eines Projekts.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Erstellen Sie ein Duplikat der Projektmappen- und Projektdateien im Versionsspeicher (freigeben und den Branch, wenn [!INCLUDE[vsvss](../../includes/vsvss-md.md)]).<br />4.  Open **Quellcodeverwaltung ändern** (Dialogfeld) (**Datei**, **Quellcodeverwaltung**, **Quellcodeverwaltung ändern**).<br />5.  Heben Sie alle.<br />6.  Klicken Sie auf **OK** schließen **Quellcodeverwaltung ändern** Dialogfeld.<br />7.  Öffnen Sie erneut **Quellcodeverwaltung ändern** Dialogfeld.<br />8.  Wählen Sie alle.<br />9. Klicken Sie auf **binden**.<br />10. Navigieren Sie zu den gebranchten Speicherort, der die Projektmappen- und Projektdateien (aus Schritt 3)<br />11. Klicken Sie auf **OK** schließen die **Quellcodeverwaltung ändern** Dialogfeld.<br />12. Rufen Sie aktuelle rekursiv für alle Elemente an.|Inhalt der Datei nach dem GET-Anforderung vor dem GET-Anforderung übereinstimmt.|  
|Binden Sie an den Speicherort, der nicht mehr synchron mit dem client|1.  Erstellen eines Projekts.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Erstellen Sie ein Duplikat der Projektmappen- und Projektdateien im Versionsspeicher (freigeben und den Branch, wenn [!INCLUDE[vsvss](../../includes/vsvss-md.md)]).<br />4.  Ändern Sie die Dateien im Projekt gebranchten im Versionsspeicher.<br />5.  Open **Quellcodeverwaltung ändern** (Dialogfeld) (**Datei**, **Quellcodeverwaltung**, **Quellcodeverwaltung ändern**).<br />6.  Heben Sie alle.<br />7.  Klicken Sie auf **OK** schließen **Quellcodeverwaltung ändern** Dialogfeld.<br />8.  Öffnen Sie erneut **Quellcodeverwaltung ändern** Dialogfeld.<br />9. Wählen Sie alle.<br />10. Klicken Sie auf **binden**.<br />11. Navigieren Sie zum Speicherort für die Projektmappe und Projekt verzweigt.<br />12. Klicken Sie auf **OK** schließen die **Quellcodeverwaltung ändern** Dialogfeld.<br />13. Akzeptieren Sie Sie im Dialogfeld Warnung, wenn er angezeigt wird.<br />14, Erhalten Sie neueste rekursiver für alle Elemente aus.|Dateien, die in Schritt 4 geändert wurden, werden auch lokal geändert.|  
|Binden Sie die Lösung, die nicht unter quellcodeverwaltung Stand|1.  Erstellen Sie einen leeren Ordner, in der quellcodeverwaltung.<br />2.  Erstellen Sie ein Clientprojekt.<br />3.  Open **Quellcodeverwaltung ändern** (Dialogfeld) (**Datei**, **Quellcodeverwaltung**, **Quellcodeverwaltung ändern**).<br />4.  Binden Sie die Lösung an leerer Speicherort in der quellcodeverwaltung an.<br />5.  Klicken Sie auf **OK** schließen die **Quellcodeverwaltung ändern** Dialogfeld.<br />6.  Klicken Sie auf **Bindungsvorgang fortsetzen** im Dialogfeld zur Bestätigung.<br />7.  Klicken Sie auf **OK** in das Warnungsdialogfeld, wenn es angezeigt wird.|Projektmappe wird zur quellcodeverwaltung hinzugefügt.<br /><br /> Projektmappen- und Projektdateien werden ausgecheckt.|  
|Cancel-Bindung|1.  Erstellen eines Projekts.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Öffnen Sie das Dialogfeld "Quellcodeverwaltung ändern".<br />4.  Heben Sie alle.<br />5.  Klicken Sie auf **OK** , um das Dialogfeld zu schließen. Wenn dieser Schritt erfolgreich ist, können Sie mit nächsten Schritt fort.<br />6.  Öffnen Sie erneut die **Quellcodeverwaltung ändern** Dialogfeld.<br />7.  Binden Sie an nicht verknüpfte Speicherort.<br />8.  Klicken Sie auf **Abbrechen**.|`Result from Step 5:`<br /><br /> Die Lösung befindet sich nicht mehr unter quellcodeverwaltung<br /><br /> `Result from Step 8:`<br /><br /> Projektmappe wird noch nicht unter quellcodeverwaltung.|  
  
### <a name="case-5b-unbind"></a>Fall 5 b: Aufheben der Bindung  
 Aufheben der Bindung entfernt Code Steuerelement Quellinformationen aus Projekten und ihre Lösung. Die betroffenen Projekte und Projektmappen basieren auf einer Kombination aus Benutzerauswahl, und wie die Elemente zur quellcodeverwaltung hinzugefügt wurden.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Bindung der Projektmappe, die ein Dateisystem oder lokalen IIS-Webprojekt und eine Client-Projekt enthält.|1.  Erstellen Sie ein Dateisystem oder dem lokalen IIS-Webprojekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Fügen Sie ein neues Clientprojekt zur Projektmappe hinzu.<br />4.  Überprüfen der Lösung akzeptieren Sie, wenn Sie aufgefordert werden.<br />5.  Öffnen der **Quellcodeverwaltung ändern** Dialogfeld.<br />6.  Klicken Sie auf **Aufheben der Bindung**.<br />7.  Klicken Sie auf **OK**, um das Dialogfeld zu schließen.<br />8.  Versuchen Sie, sehen Sie sich die Lösung "," Projekt "," Projektmappenelemente "," Projektelemente.|Projektmappen und Projekte sind nicht unter quellcodeverwaltung.<br /><br /> Quellcodeverwaltungsbefehle Menü nicht angezeigt.|  
|Aufheben der Bindung "Abbrechen"|1.  Erstellen eines Projekts.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Öffnen der **Quellcodeverwaltung ändern** Dialogfeld.<br />4.  Klicken Sie auf **Bindung alle**.<br />5.  Klicken Sie auf **Abbrechen**.|Lösung besteht in der quellcodeverwaltung.|  
  
### <a name="case-5c-rebind"></a>Fall 5c: erneut binden  
 Binden ist einfach eine Kombination von Bindung aufheben und Bind – der Prozess der durch das erneute Binden einer Projekt/Projektmappe, die zuvor in der quellcodeverwaltung wurde aufgehoben.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Binden von Projektmappen und Projekte lassen die **Quellcodeverwaltung ändern** (Dialogfeld)|1.  Erstellen eines Projekts.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Öffnen der **Quellcodeverwaltung ändern** Dialogfeld.<br />4.  Klicken Sie auf **Aufheben der Bindung**.<br />5.  Alle Zeilen auswählen.<br />6.  Klicken Sie auf **binden**.<br />7.  Klicken Sie auf **OK** schließen die **Quellcodeverwaltung ändern** Dialogfeld.<br />8.  Akzeptieren Sie auschecken, wenn Sie aufgefordert werden.|Projektmappen- und Projektdateien, die unter quellcodeverwaltung stehen.|  
|Rebind-Projekt nur ohne schließendes **Quellcodeverwaltung ändern** (Dialogfeld)|1.  Erstellen eines Projekts.<br />2.  Fügen Sie nur das Projekt mit Datenquelle Steuerelement mit (Datei -> Source Control -> ausgewählte Projekte zur Quellcodeverwaltung hinzufügen.<br />3.  Öffnen Sie das Dialogfeld "Quellcodeverwaltung ändern".<br />4.  Heben Sie nur das Projekt ein.<br />5.  Binden Sie nur das Projekt ein.|Lösung bleibt unkontrollierten.<br /><br /> Projekt bleibt die gesteuerten.|  
|Binden Sie die Projektmappe nur ohne schließendes **Quellcodeverwaltung ändern** (Dialogfeld)|1.  Erstellen eines Projekts.<br />2.  Fügen Sie nur die Lösung zur Verwendung von Source Control (**Datei**, **Quellcodeverwaltung**, **ausgewählte Projekte zur Quellcodeverwaltung hinzufügen**.<br />3.  Öffnen der **Quellcodeverwaltung ändern** Dialogfeld.<br />4.  Aufheben der Bindung nur der Lösung (Schließen Sie nicht **Quellcodeverwaltung ändern** Dialogfeld.)<br />5.  Binden Sie nur die Lösung.<br />6.  Klicken Sie auf **OK**, um das Dialogfeld zu schließen.<br />7.  Sehen Sie sich Lösung und Projektmappenelemente (sofern vorhanden.)|Lösung bleibt die gesteuerten.<br /><br /> Projekt bleibt unkontrollierten.|  
|Binden Sie die Projektmappe oder eines Projekts nur im gleichen Verzeichnis|1.  Erstellen eines Projekts.<br />2.  Fügen Sie nur das Projekt mit Source Control (**Datei**, **Quellcodeverwaltung**, **ausgewählte Projekte zur Quellcodeverwaltung hinzufügen**.<br />3.  Schließen Sie die Projektmappe.<br />4.  Erstellen Sie eine neue Projektmappe mit mindestens zwei Projekte.<br />5.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />6.  Fügen Sie das Projekt in Schritt 1 erstellt haben, aus der quellcodeverwaltung hinzu.<br />7.  Akzeptieren Sie das Auschecken der Lösung, wenn Sie aufgefordert werden.<br />8.  Überprüfen Sie in der gesamten Projektmappe.<br />9. Öffnen der **Quellcodeverwaltung ändern** Dialogfeld.<br />10. Wählen Sie das hinzugefügte Projekt (aus Schritt 6), und klicken Sie auf **Unbind**.<br />11. Klicken Sie auf **OK**, um das Dialogfeld zu schließen.<br />12. Akzeptieren Sie das Auschecken, wenn Sie aufgefordert werden.<br />13. Öffnen Sie erneut **Quellcodeverwaltung ändern** Dialogfeld.<br />14, Wählen Sie das hinzugefügte Projekt (aus Schritt 6), und klicken Sie auf **binden**.<br />15. Wählen Sie am ursprünglichen Speicherort.|Projektmappen und Projekte bleiben kontrollierten.|  
  
## <a name="see-also"></a>Siehe auch  
 [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

