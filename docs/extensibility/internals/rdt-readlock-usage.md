---
title: RDT_ReadLock Nutzung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb897fab61e1e14b52863b5853748c685200d5ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705926"
---
# <a name="rdt_readlock-usage"></a>RDT_ReadLock-Verwendung

[_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) ist ein Flag, das Logik zum Sperren eines Dokuments in der Running Document Table (RDT) bereitstellt, d. h. die Liste aller Dokumente, die derzeit in der Visual Studio-IDE geöffnet sind. Dieses Flag bestimmt, wann Dokumente geöffnet werden und ob ein Dokument in der Benutzeroberfläche sichtbar ist oder unsichtbar im Arbeitsspeicher gespeichert ist.

Im Allgemeinen verwenden Sie [_VSRDTFLAGS. RDT_ReadLock,](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) wenn eine der folgenden Optionen zutrifft:

- Sie möchten ein Dokument unsichtbar und schreibgeschützt öffnen, aber <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> es ist noch nicht festgelegt, welches es besitzen soll.

- Sie möchten, dass der Benutzer aufgefordert wird, ein Dokument zu speichern, das unsichtbar geöffnet wurde, bevor der Benutzer es in der Benutzeroberfläche angezeigt und dann versucht hat, es zu schließen.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Verwalten von sichtbaren und unsichtbaren Dokumenten

Wenn ein Benutzer ein Dokument in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> der Benutzeroberfläche öffnet, muss ein Besitzer für das Dokument eingerichtet und ein [_VSRDTFLAGS. RDT_EditLock-Flag](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) muss gesetzt werden. Wenn <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> kein Besitzer eingerichtet werden kann, wird das Dokument nicht gespeichert, wenn der Benutzer auf **Alle speichern** klickt oder die IDE schließt. Dies bedeutet, wenn ein Dokument unsichtbar geöffnet ist, wenn es im Arbeitsspeicher geändert **Save All** wird, und der `RDT_ReadLock` Benutzer aufgefordert wird, das Dokument beim Herunterfahren zu speichern oder zu speichern, wenn Alle speichern ausgewählt ist, kann keine verwendet werden. Stattdessen müssen Sie `RDT_EditLock` eine verwenden <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> und registrieren, wenn ein [__VSREGDOCLOCKHOLDER. RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) Flagge.

## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock und Dokumentänderung

Das erwähnte vorherige Flag gibt an, dass `RDT_EditLock` das unsichtbare Öffnen des Dokuments nachlässt, wenn das Dokument vom Benutzer in ein sichtbares **DocumentWindow**geöffnet wird. In diesem Fall wird dem Benutzer eine **Eingabeaufforderung speichern** angezeigt, wenn das sichtbare **DocumentWindow** geschlossen wird. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel`Implementierungen, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> den Dienst verwenden, funktionieren zunächst, wenn nur ein `RDT_ReadLock` übernommen wird (d. h., wenn das Dokument unsichtbar geöffnet wird, um Informationen zu analysieren). Wenn das Dokument später geändert werden muss, wird die Sperre auf eine schwache **RDT_EditLock**aktualisiert. Wenn der Benutzer dann das Dokument in `CodeModel`einem sichtbaren **DocumentWindow**öffnet, wird die Schwachstelle `RDT_EditLock` von 's freigegeben.

Wenn der Benutzer dann das **DocumentWindow** schließt und **Nein** auswählt, `CodeModel` wenn er aufgefordert wird, das geöffnete Dokument zu speichern, werden in der Implementierung alle Informationen im Dokument gespeichert, und das Dokument wird unsichtbar wieder geöffnet, wenn das nächste Mal weitere Informationen für das Dokument benötigt werden. Die Subtilität dieses Verhaltens ist eine Instanz, in der der Benutzer das **DocumentWindow** des unsichtbaren geöffneten Dokuments öffnet, es ändert, es schließt und dann **Nein** auswählt, wenn er zum Speichern des Dokuments aufgefordert wird. In diesem Fall wird das `RDT_ReadLock`Dokument, wenn das Dokument über eine verfügt, nicht geschlossen, und das geänderte Dokument bleibt unsichtbar im Arbeitsspeicher geöffnet, obwohl der Benutzer das Dokument nicht gespeichert hat.

Wenn die unsichtbare Öffnung des `RDT_EditLock`Dokuments eine schwache verwendet, dann gibt sie ihre Sperre ab, wenn der Benutzer das Dokument sichtbar öffnet und keine anderen Sperren gehalten werden. Wenn der Benutzer das **DocumentWindow** schließt und **Nein** auswählt, wenn er zum Speichern des Dokuments aufgefordert wird, muss das Dokument aus dem Arbeitsspeicher geschlossen werden. Dies bedeutet, dass der unsichtbare Client auf RDT-Ereignisse warten muss, um dieses Vorkommen nachzuverfolgen. Wenn das Dokument das nächste Mal benötigt wird, muss es erneut geöffnet werden.
