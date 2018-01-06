---
title: Lock-Inhaber dokumentverwaltung | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: df782cd974adcd589824e8a47cd0249842bd8d48
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="document-lock-holder-management"></a>Inhaber von Dokumentverwaltung-Sperre
Ausgeführt Dokument Tabelle (RDT) verwaltet die Anzahl der geöffneten Dokumente und Sperren bearbeiten, die sie besitzen. Sie können eine Bearbeiten-Sperre für ein Dokument in der RDT platzieren, wenn es programmgesteuert im Hintergrund ohne dass der Benutzer sehen ein geöffnetes Dokument in einem Dokumentfenster bearbeitet wird. Diese Funktionalität wird häufig von Entwicklern verwendet, die mehrere Dateien über eine grafische Benutzeroberfläche zu ändern.  
  
## <a name="document-lock-holder-scenarios"></a>Dokument Inhaber-Szenarien  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>Datei "a" hat eine Abhängigkeit von der Datei "b"  
 Betrachten Sie eine Situation, in dem Sie eine standard-Editors "A" für den Dateityp implementieren "a", und jede Datei vom Typ "a" ist ein Verweis auf (oder die Abhängigkeit) eine Datei des Typs "b". Für Dateien vom Typ "b" ist ein standard-Editors "B" vorhanden. Beim Öffnen von Editor "A"-Datei Ruft den Verweis auf die entsprechende Datei "b" von "a" It ab. Datei "b" wird nicht angezeigt, aber "A"-Editor ändern kann. -Editor "ein" erhält einen Verweis auf die Daten der Datei "b" aus der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> Methode und verwaltet auch eine Bearbeiten-Sperre für die Datei "b". Nach Abschluss der Editor "A" ändern die Datei "b" können Sie die Sperre bearbeiten Dekrementieren Verweiszählers für Datei "b" durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> Methode. Sie können diesen Schritt auslassen, wenn Sie aufgerufen hätten die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> Methode mit dem Parameter `dwRDTLockType` festgelegt <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>Die Datei "b" wird von einem anderen Editor geöffnet.  
 Wenn die Datei "b" bereits geöffnet wird, vom Editor "B" Wenn-Editor "A" versucht, ihn zu öffnen, es gibt zwei separate Szenarien behandelt:  
  
-   Wenn die Datei "b" in einen kompatiblen Editor geöffnet ist, benötigen Sie Editor "A" registrieren Sie eine Dokument bearbeiten-Sperre für die Datei "b" mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> Methode. Nachdem der Editor "A" Ändern von Datei "b" erfolgt ist, Aufheben der Registrierung des Dokuments bearbeiten Sperre mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> Methode.  
  
-   Wenn die Datei "b" in eine nicht kompatible Weise geöffnet ist, können Sie entweder das versuchte Öffnen der Datei "b" vom Editor lassen "A" fehl, oder Sie die zugeordnete-Editor lassen "A" teilweise öffnen und Anzeigen einer entsprechenden Fehlermeldung an. Die Fehlermeldung sollte den Benutzer anweisen, schließen Sie die Datei "b" in der nicht kompatiblen Editor, und öffnen die Datei mithilfe von "a" klicken Sie dann erneut Editor "A". Sie können auch implementieren die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Methode <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> abgefragt, die Datei "b" zu schließen, die in der nicht kompatiblen Editor geöffnet ist. Wenn der Benutzer die Datei "b", das Öffnen der Datei schließt wird "a" in Editor "A" normal fortgesetzt.  
  
## <a name="additional-document-edit-lock-considerations"></a>Zusätzliche Dokument bearbeiten Sperre Überlegungen  
 Erhalten Sie unterschiedliches Verhalten, wenn Editor "A" der einzige Editor, der ein Dokument, die Sperre für die Datei "b" zu bearbeiten ist, als würden Editor "B" enthält auch ein Dokument hat bearbeiten Sperre für die Datei "b". In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], **Klassen-Designer** ist ein Beispiel eines visuellen Designers, der eine Sperre für die Bearbeitung nicht auf der zugeordneten Codedatei enthält. D. h. gehen verloren, wenn der Benutzer muss ein Klassendiagramm öffnen Sie in der Entwurfsansicht und die zugeordneten Codedatei gleichzeitig öffnen, und wenn der Benutzer ändert die Codedatei, aber die Änderungen nicht gespeichert, die Änderungen auch in der Klassendatei für die Klassendiagrammdatei (). Wenn die **Klassen-Designer** hat nur Sperren auf die Codedatei zu bearbeiten, der Benutzer wird nicht aufgefordert, die Änderungen zu speichern, schließen Sie die Codedatei. Die IDE fordert den Benutzer auf die Änderungen zu speichern, nachdem der Benutzer schließt den **Klassen-Designer**. Die gespeicherten Änderungen werden in beiden Dateien angezeigt. Wenn beide die **Klassen-Designer** und der Code-Editor auf die Codedatei Dokument bearbeiten Sperren aufrechterhalten, und der Benutzer aufgefordert wird, um beim Schließen der Codedatei oder das Formular zu speichern. An diesem Punkt werden die Änderungen gespeicherten, in das Formular und die Codedatei wiedergegeben. Weitere Informationen in Klassendiagrammen finden Sie unter [arbeiten mit Klassendiagrammen (Klassen-Designer)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Beachten Sie, dass wenn Sie eine Bearbeiten-Sperre für ein Dokument für einen Editor platzieren möchten, müssen Sie implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> Schnittstelle.  
  
 Oft ein UI-Designer, der die Codedateien programmgesteuert ändert nimmt Änderungen an mehr als eine Datei. In solchen Fällen das <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> Methode behandelt das Speichern von einem oder mehreren Dokumenten mithilfe von der **möchten Sie die folgenden Elemente speichern?** (Dialogfeld).  
  
## <a name="see-also"></a>Siehe auch  
 [Dokumenttabelle der ausgeführten](../extensibility/internals/running-document-table.md)   
 [Persistenz und die aktive Dokumenttabelle](../extensibility/internals/persistence-and-the-running-document-table.md)