---
title: Dokument-Sperrhalter-Management | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9dd520f8ad5cab1f0cfee890c4bcc388c204bb1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712126"
---
# <a name="document-lock-holder-management"></a>Verwaltung von Dokumentenschlosshaltern

Die laufende Dokumenttabelle (RDT) verwaltet eine Anzahl geöffneter Dokumente und aller Bearbeitungssperren. Sie können eine Bearbeitungssperre für ein Dokument im RDT platzieren, wenn es programmgesteuert im Hintergrund bearbeitet wird, ohne dass der Benutzer ein geöffnetes Dokument in einem Dokumentfenster sieht. Diese Funktionalität wird häufig von Designern verwendet, die mehrere Dateien über eine grafische Benutzeroberfläche ändern.

## <a name="document-lock-holder-scenarios"></a>Dokumentsperrhalter-Szenarien

### <a name="file-a-has-a-dependence-on-file-b"></a>Datei "a" hat eine Abhängigkeit von Datei "b"

Betrachten Sie eine Situation, in der Sie einen Standard-Editor "A" für den Dateityp "a" implementieren, und jede Datei des Typs "a" einen Verweis auf (oder Abhängigkeit von) einer Datei vom Typ "b" enthält. Für Dateien vom Typ "b" ist ein Standardeditor "B" vorhanden. Wenn Editor "A" die Datei "a" öffnet, ruft er den Verweis auf die entsprechende Datei "b" ab. Datei "b" wird nicht angezeigt, aber Editor "A" kann es ändern. Editor "A" ruft einen Verweis auf die Dokumentdaten <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> der Datei "b" von der Methode ab und behält auch eine Bearbeitungssperre für die Datei "b" bei. Nachdem Editor "A" mit dem Ändern der Datei "b" fertig ist, können Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> die Anzahl der Bearbeitungssperren für die Datei "b" dekrementieren, indem Sie die Methode aufrufen. Sie können diesen Schritt weglassen, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> wenn Sie `dwRDTLockType` die Methode aufgerufen haben, wobei der Parameter auf _VSRDTFLAGS festgelegt [ist. RDT_NoLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_NoLock>).

### <a name="file-b-is-opened-by-a-different-editor"></a>Datei "b" wird von einem anderen Editor geöffnet

Für den Fall, dass die Datei "b" bereits vom Editor "B" geöffnet wird, wenn Editor "A" versucht, sie zu öffnen, gibt es zwei separate Szenarien zu behandeln:

- Wenn die Datei "b" in einem kompatiblen Editor geöffnet ist, müssen Sie den Editor <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> "A" mit der Methode eine Dokumentbearbeitungssperre für die Datei "b" registrieren lassen. Nachdem Ihr Editor "A" mit dem Ändern der Datei "b" <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> abgeschlossen ist, heben Sie die Registrierung der Dokumentbearbeitungssperre mit der Methode auf.

- Wenn die Datei "b" in kompatibel geöffnet ist, können Sie entweder das versuchte Öffnen der Datei "b" durch den Editor "A" fehlschlagen lassen, oder Sie können die dem Editor "A" zugeordnete Ansicht teilweise öffnen lassen und eine entsprechende Fehlermeldung anzeigen. Die Fehlermeldung sollte den Benutzer anweisen, die Datei "b" im inkompatiblen Editor zu schließen und dann die Datei "a" mit dem Editor "A" erneut zu öffnen. Sie können auch [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> die Methode implementieren, um den Benutzer zum Schließen der Datei "b" aufzufordern, die im inkompatiblen Editor geöffnet ist. Wenn der Benutzer die Datei "b" schließt, wird das Öffnen der Datei "a" im Editor "A" normal fortgesetzt.

## <a name="additional-document-edit-lock-considerations"></a>Zusätzliche Überlegungen zur Dokumentbearbeitungssperre

Sie erhalten ein anderes Verhalten, wenn Editor "A" der einzige Editor ist, der eine Dokumentbearbeitungssperre für die Datei "b" hat, als wenn Editor "B" auch eine Dokumentbearbeitungssperre für die Datei "b" hat. In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ist **Class Designer** ein Beispiel für einen visuellen Designer, der keine Bearbeitungssperre für die zugehörige Codedatei enthält. Das heißt, wenn der Benutzer ein Klassendiagramm in der Entwurfsansicht geöffnet hat und die zugehörige Codedatei gleichzeitig geöffnet ist und der Benutzer die Codedatei ändert, die Änderungen jedoch nicht speichert, gehen die Änderungen auch an die Klassendiagrammdatei (.cd) verloren. Wenn der **Klassen-Designer** die einzige Dokumentbearbeitungssperre für die Codedatei hat, wird der Benutzer nicht aufgefordert, die Änderungen beim Schließen der Codedatei zu speichern. Die IDE fordert den Benutzer auf, die Änderungen erst zu speichern, nachdem der Benutzer den **Klassen-Designer**geschlossen hat. Die gespeicherten Änderungen werden in beiden Dateien widergespiegelt. Wenn sowohl der **Klassen-Designer** als auch der Codedatei-Editor die Codedatei gesperrt haben, wird der Benutzer aufgefordert, beim Schließen der Codedatei oder des Formulars zu speichern. An diesem Punkt werden die gespeicherten Änderungen sowohl im Formular als auch in der Codedatei widergespiegelt. Weitere Informationen zu Klassendiagrammen finden Sie unter [Arbeiten mit Klassendiagrammen (Klassen-Designer)](../ide/class-designer/designing-and-viewing-classes-and-types.md).

Wenn Sie eine Bearbeitungssperre für ein Dokument für einen Nicht-Editor <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> platzieren müssen, müssen Sie die Schnittstelle implementieren.

Häufig nimmt ein UI-Designer, der Codedateien programmgesteuert ändert, Änderungen an mehr als einer Datei vor. In solchen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> Fällen übernimmt die Methode das Speichern eines oder mehrerer Dokumente über das Dialogfeld **Änderungen an den folgenden Elementen speichern?**

## <a name="see-also"></a>Weitere Informationen

- [Ausführen der Dokumenttabelle](../extensibility/internals/running-document-table.md)
- [Persistenz und die laufende Dokumenttabelle](../extensibility/internals/persistence-and-the-running-document-table.md)
