---
title: "Verwaltung der Inhaber Dokument | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] benutzerdefinierte - Dokument sperren"
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Verwaltung der Inhaber Dokument
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die ausgeführte Drehtransformator Tabelle aktiver Dokumente \(\) verwaltet eine Anzahl geöffnete Dokumente und jede Bearbeitung gesperrt haben.  Sie können eine sperre Bearbeiten auf einem Dokument in Drehtransformator platzieren, wenn dies programmgesteuert im Hintergrund ohne den Benutzer bearbeitet wird, der einem geöffneten Dokument in einem Dokumentfenster anzuzeigen.  Diese Funktionalität wird häufig verwendet, um die vom Designer mehrere Dateien über eine grafische Benutzeroberfläche ändern.  
  
## Dokumenten\-Sperren\-Halter\-Szenarien  
  
### Datei „a“ hat eine Abhängigkeit für die Datei „b“  
 Betrachten Sie eine Situation, in der Sie einen standardmäßigen Editor „A“ für Dateityp „a“ implementieren, und jede Datei vom Typ „a“ weist einen Verweis auf \(oder Abhängigkeit\) einer Datei vom Typ „b“.  Ein Standardwert des Editors „B“ ist für Dateien vom Typ „b“.  Wenn Editor „A“ Datei „a“ öffnet, kann sie den Verweis auf die entsprechende Datei „b“ ab.  Datei „b“ wird nicht angezeigt, aber Editor „A“ kann sie ändern.  Editor „A“ wird ein Verweis auf den Dokumenten von Daten aus Datei „b“ aus der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>\-Methode und wartet auf sperre Bearbeiten außerdem die Datei „b“.  Nach dem Editor „A“ wird die Datei „b“ ändern, können Sie die sperrenanzahl Bearbeiten auf die Datei „b“ verringern, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>\-Methode aufrufen.  Sie können diesen Schritt auslassen, wenn Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>\-Methode mit dem Parameter `dwRDTLockType` festgelegt <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>aufgerufen hätten.  
  
### Datei „b“ wird von einem anderen Editor geöffnet  
 Im Fall, dass die Datei „b“ Editor „B“ bereits durch geöffnet wird, wenn Editor „A“ wird versucht, diesen zu öffnen, gibt es zwei verschiedene Szenarios behandelt:  
  
-   Wenn die Datei „b“ in einen kompatiblen Editor geöffnet ist, müssen Sie zum Registrieren des Editors „A“ eine Dokumenten bearbeitungs sperre auf die Datei „b“ mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>\-Methode verfügen.  Nachdem der Editor „A“ wird die Datei „b“ UN Ändern sperre bearbeitungs die Register mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>\-Methode.  
  
-   Wenn die Datei „b“ auf eine nicht kompatible Weise geöffnet ist, können Sie können die versuchte Öffnen der Datei „b“ durch „A“ Fail des Editors, oder Sie können die Ansicht, die mit teilweiser Editor „A“ eine entsprechende Fehlermeldung zu öffnen und anzeigen.  Die Fehlermeldung sollte den Benutzer anweisen, Datei „b“ in nicht kompatiblen Editor zu schließen und die Datei mit „a“ Editor „A“ anschließend erneut zu öffnen.  Sie können das [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]\-Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> ebenfalls implementieren, um den Benutzer aufzufordern, Datei „b“ zu schließen, die in nicht kompatiblen Editor geöffnet ist.  Wenn der Benutzer die Datei „b“ umfasst, wird die Start\- Datei „a“ in Editor „A“ normalerweise fort.  
  
## Weitere Dokumenten\-Bearbeitungs\-Sperren\-Überlegungen  
 Rufen Sie ein anderes Verhalten ab, wenn Editor „A“ ist der einzige Editor Dokumente, der eine bearbeitungs sperre auf die Datei „b“ hat, als Sie wurden, wenn Editor „B“ auch eine bearbeitungs Dokumente sperre auf die Datei „b“ enthält.  In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]**Klassen\-Designer** ist ein Beispiel eines visuellen Designers, der keine sperre Bearbeiten auf der zugeordneten Codedatei enthält.  Das heißt, wenn der Benutzer ein Klassendiagramm enthält, das in der Entwurfsansicht geöffnet sind und die zugeordnete Codedatei, die gleichzeitig geöffnet ist und der Benutzer die Codedatei ändert, jedoch nicht die Änderungen gespeichert werden sollen, sind auch die Änderungen an der Klassendiagrammdatei \(CD\-Datei\) verloren.  Wenn **Klassen\-Designer** die einzige Dokumenten bearbeitungs sperre in der Codedatei wurde, wird der Benutzer nicht aufgefordert, die Änderungen zu speichern, wenn Sie die Codedatei schließt.  Die IDE fordert den Benutzer Änderungen zu speichern, die erst nach der Benutzer **Klassen\-Designer**geschlossen wird.  Die gespeicherten Änderungen werden in beiden Dateien wiedergibt.  Wenn **Klassen\-Designer** und der Codedatei des Editors reservierten Bearbeiten von Dokumenten, Sperren auf die Codedatei, wird der Benutzer aufgefordert zu speichern, wenn entweder die Codedatei oder das Formular geschlossen wird.  An diesem Punkt werden die gespeicherten Änderungen in der Form und in der Codedatei wiedergegeben.  Weitere Informationen zu Klassendiagrammen finden Sie unter [Working with Class Diagrams \(Class Designer\)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Beachten Sie, dass, wenn Sie eine sperre Bearbeiten auf einem Dokument für einen nicht Editor einfügen müssen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>\-Schnittstelle implementieren müssen.  
  
 Viele Mal wird ein Benutzeroberfläche\-Designer, Codedateien programmgesteuert geändert wird, Änderungen an mehr als einer Datei vor.  In einem solchen Fall behandelt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>\-Methode die Speichern eines oder mehrerer Dokumente mithilfe des Dialogfelds **Möchten Sie die Änderungen für die folgenden Elemente speichern?** .  
  
## Siehe auch  
 [Dokumenttabelle der ausgeführten](../extensibility/internals/running-document-table.md)   
 [Persistenz und der Document\-Tabelle ausgeführt wird](../extensibility/internals/persistence-and-the-running-document-table.md)