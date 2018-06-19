---
title: Verwendung von RDT_ReadLock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fda2fbb4a4b03dff9d677d9c7581a4138d9fcf7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131680"
---
# <a name="rdtreadlock-usage"></a>RDT_ReadLock Verwendung

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> ist ein Flag, das Logik bereitstellt, für das Sperren eines Dokuments in der Ausführung Dokument Tabelle (RDT), also in der Liste aller Dokumente, die derzeit in der Visual Studio IDE geöffnet sind. Dieses Flag bestimmt, wenn Dokumente geöffnet sind, und gibt an, ob ein Dokument in der Benutzeroberfläche sichtbar oder unsichtbar im Arbeitsspeicher gehalten wird.

Im Allgemeinen verwenden Sie <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> , wenn eines der folgenden Aussagen zutrifft:

- Wenn Sie ein Dokument unsichtbar öffnen möchten und Read-only, aber es wird noch nicht eingerichtet, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> sollte der Besitzer.

- Wenn Sie den Benutzer zur Eingabe aufgefordert, ein Dokument zu speichern, die im Hintergrund geöffnet wurde, bevor der Benutzer sie in der Benutzeroberfläche angezeigt, und anschließend wurde versucht, ihn schließen möchten.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Gewusst wie: Verwalten von Dokumenten für sichtbar und unsichtbar

Wenn ein Benutzer ein Dokument in der Benutzeroberfläche öffnet ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Besitzer für das Dokument muss eingerichtet werden, und ein <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> Flag muss festgelegt werden. Wenn kein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Besitzer hergestellt werden kann, und klicken Sie dann das Dokument wird nicht gespeichert werden, wenn der Benutzer klickt **alle speichern** oder schließt die IDE. Dies bedeutet, wenn ein Dokument unsichtbar geöffnet, ist wobei es im Arbeitsspeicher geändert wird, und der Benutzer aufgefordert, die zum Speichern des Dokuments beim Herunterfahren oder gespeichert, wenn **alle speichern** ausgewählt wird, wird eine `RDT_ReadLock` kann nicht verwendet werden. Stattdessen müssen Sie verwenden ein `RDT_EditLock` und registrieren Sie eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> Wenn ein <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> Flag.

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock und Änderung von Dokumenten

Das vorherige Flag erwähnt gibt an, dass das unsichtbare Öffnen des Dokuments gibt seine `RDT_EditLock` beim Öffnen des Dokuments durch den Benutzer in ein sichtbares **DocumentWindow**. In diesem Fall erhält der Benutzer mit einer **speichern** aufgefordert, wenn die sichtbaren **DocumentWindow** geschlossen wird. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` Implementierungen, mit denen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> Dienst anfänglich zu funktionieren, wenn nur ein `RDT_ReadLock` stammt (d. h. beim Öffnen des Dokuments nicht sichtbar ist, um Informationen zu analysieren). Später, wenn das Dokument geändert werden muss, klicken Sie dann die Sperre wird aktualisiert auf eine schwache **RDT_EditLock**. Wenn der Benutzer das Dokument in ein sichtbares dann öffnet **DocumentWindow**, die `CodeModel`des schwachen `RDT_EditLock` freigegeben wird.

Wenn der Benutzer dann schließt die **DocumentWindow** und wählt **keine** bei der Aufforderung zum Speichern der geöffneten Dokuments die `CodeModel` Implementierung verwirft alle Informationen im Dokument und wieder öffnet die Dokument vom Datenträger unsichtbar das nächste Mal, das Informationen für das Dokument erforderlich ist. Der Besonderheit der dieses Verhalten ist eine Instanz, in denen der Benutzer öffnet, die **DocumentWindow** des unsichtbaren geöffneten Dokuments ändert, wird geschlossen und wählt dann **keine** bei der Aufforderung zum Speichern des Dokuments. In diesem Fall, wenn das Dokument besitzt eine `RDT_ReadLock`, klicken Sie dann das Dokument wird nicht geschlossen werden, und das geänderte Dokument wird unsichtbar im Arbeitsspeicher, geöffnet bleiben, auch wenn der Benutzer hat nicht das Dokument zu speichern.

Wenn das unsichtbare Öffnen des Dokuments eine schwache verwendet `RDT_EditLock`, dann gibt er seine Sperre, wenn der Benutzer das Dokument sichtbar geöffnet und keine anderen Sperren aufrechterhalten werden. Der Benutzer schließt den **DocumentWindow** und wählt **keine** Aufforderung zum Speichern des Dokuments, klicken Sie dann das Dokument muss geschlossen werden, aus dem Arbeitsspeicher. Dies bedeutet, dass es sich bei der unsichtbar Client RDT Ereignisse zum Nachverfolgen von genau überwachen muss. Das nächste Mal das Dokument erforderlich ist, muss das Dokument erneut geöffnet werden.