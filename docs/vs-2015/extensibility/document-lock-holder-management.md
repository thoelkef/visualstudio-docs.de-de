---
title: Dokumentieren Sie die Verwaltung von Dokumentsperren | Microsoft-Dokumentation
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
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8eaeb8529f570db112bf43813fe20339f3bca7c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786300"
---
# <a name="document-lock-holder-management"></a>Verwaltung von Dokumentsperren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der ausgeführten Dokumenttabelle (RDT) verwaltet die Anzahl der geöffneten Dokumente und bearbeitungssperren, die Sie. Sie können eine Bearbeitungssperre in einem Dokument im RDT platzieren, wenn sie programmgesteuert im Hintergrund ohne dass der Benutzer sehen ein geöffnetes Dokument in einem Dokumentfenster bearbeitet wird. Diese Funktion wird häufig von Designern verwendet werden, die mehrere Dateien über eine grafische Benutzeroberfläche zu ändern.  
  
## <a name="document-lock-holder-scenarios"></a>Dokument Inhaber-Szenarien  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>Datei "a" verfügt über eine Abhängigkeit von Datei "b"  
 Betrachten Sie eine Situation, in dem Sie einen standard-Editor "A" für den Dateityp implementieren "a", und jede Datei vom Typ "a" ist ein Verweis auf (oder eine Abhängigkeit) eine Datei vom Typ "b". Ein standard-Editor "B" ist für Dateien vom Typ "b" vorhanden. "A" It Ruft den Verweis auf die entsprechende Datei "b" ab, wenn "A"-Editor die Datei geöffnet wird. Datei "b" wird nicht angezeigt, aber "A"-Editor kann geändert werden. -Editor "ein" Ruft einen Verweis auf die Daten der Datei "b" aus der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> Methode und verwaltet auch eine Bearbeitungssperre für Datei "b". Ändern die Datei "b" können Sie die Bearbeitungssperre Dekrementieren nach Abschluss der Editor "A" ist auf die Datei "b" durch den Aufruf zählen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> Methode. Können Sie diesen Schritt weglassen, wenn Sie hätten die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> Methode mit dem Parameter `dwRDTLockType` festgelegt <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>Datei "b" wird von einem anderen Editor geöffnet.  
 Wenn die Datei "b" bereits geöffnet wird, vom-Editor "B" Wenn-Editor "A" versucht wird, um ihn zu öffnen, es gibt zwei separate Szenarien behandelt:  
  
-   Wenn die Datei "b" in einen kompatiblen Editor geöffnet ist, benötigen Sie Editor "A" registrieren Sie ein Dokument Bearbeitungssperre zur Verwendung der Datei "b" der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> Methode. Nachdem Ihr Editor "A" Ändern von Datei "b" erfolgt ist, Aufheben der Registrierung des Dokuments bearbeiten Sperre der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> Methode.  
  
-   Wenn die Datei "b" in eine nicht kompatible Weise geöffnet ist, können Sie entweder das versuchte Öffnen der Datei "b" von Editor lassen "A" ein, oder Sie die zugeordnete-Editor lassen "A" teilweise öffnen und Anzeigen einer entsprechenden Fehlermeldung an. Die Fehlermeldung sollte den Benutzer anweisen, schließen Sie die Datei "b" in der nicht kompatiblen Editor, und öffnen die Datei mithilfe von "a" klicken Sie dann erneut Editor "A". Sie können auch implementieren die [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Methode <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> mit benutzeraufforderung, Datei "b" zu schließen, die in der nicht kompatiblen Editor geöffnet ist. Wenn der Benutzer die Datei "b", das Öffnen der Datei schließt Weiter "a" im Editor "A" Normal.  
  
## <a name="additional-document-edit-lock-considerations"></a>Zusätzliche Dokument bearbeiten Sperre Überlegungen  
 Erhalten Sie anderes Verhalten, wenn der Editor "A" ist die einzige Editor, in dem ein Dokument, die Sperre für die Datei "b" zu bearbeiten, als bei der Editor "B" auch ein Dokument enthält Bearbeitungssperre Datei "b". In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], **Klassen-Designer** ist ein Beispiel mit einem visuellen Designer, die keine Bearbeitungssperre auf der zugeordneten Codedatei enthalten ist. D. h. verloren, wenn der Benutzer hat ein Klassendiagramm in der Entwurfsansicht öffnen, und die zugeordneten Codedatei gleichzeitig öffnen, und wenn der Benutzer ändert die Codedatei, aber die Änderungen nicht gespeichert, die Änderungen auch auf die Klassendiagrammdatei (CD). Wenn die **Klassen-Designer** verfügt das Dokument nur Bearbeitungssperre der Codedatei zu verlassen, wird nicht der Benutzer zum Speichern der Änderungen beim Schließen der Codedatei aufgefordert. Die IDE fordert den Benutzer auf die Änderungen zu speichern, nur, nachdem der Benutzer schließt die **Klassen-Designer**. Die gespeicherte Änderungen werden in beiden Dateien angezeigt. Wenn beide die **Klassen-Designer** und der Code-Editor bearbeitungssperren Dokument auf der Codedatei gespeichert, und klicken Sie dann die Benutzer aufgefordert wird, speichern, wenn der Codedatei oder das Formular zu schließen. An diesem Punkt sind die gespeicherten Änderungen in das Formular und die Codedatei angezeigt. Weitere Informationen in Klassendiagrammen finden Sie unter [arbeiten mit Klassendiagrammen (Klassen-Designer)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Beachten Sie, dass wenn Sie eine Bearbeitungssperre in einem Dokument für einen nicht-Editor platzieren möchten, müssen Sie implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> Schnittstelle.  
  
 Oft ein Benutzeroberflächen-Designer, der Codedateien programmgesteuert ändert nimmt Änderungen an mehr als eine Datei. In solchen Fällen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> Methode verarbeitet das Speichern von ein oder mehrere Dokumente mithilfe von der **möchten Sie die folgenden Elemente speichern?** Dialogfeld.  
  
## <a name="see-also"></a>Siehe auch  
 [Aktive Dokumenttabelle](../extensibility/internals/running-document-table.md)   
 [Persistenz und die aktive Dokumenttabelle](../extensibility/internals/persistence-and-the-running-document-table.md)

