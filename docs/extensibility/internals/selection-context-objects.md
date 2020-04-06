---
title: Auswahl kontextobjekte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e4f33dd0168a667b8f266ea606cecf0c26d62f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705508"
---
# <a name="selection-context-objects"></a>Auswahlkontextobjekte
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE) verwendet ein globales Auswahlkontextobjekt, um zu bestimmen, was in der IDE angezeigt werden soll. Jedes Fenster in der IDE kann sein eigenes Auswahlkontextobjekt in den globalen Auswahlkontext übertragen haben. Die IDE aktualisiert den globalen Auswahlkontext mit Werten aus einem Fenster, wenn dieses Fenster den Fokus hat. Weitere Informationen finden Sie unter [Feedback an den Benutzer](../../extensibility/internals/feedback-to-the-user.md).

 Jeder Fensterrahmen oder Standort in der <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>IDE verfügt über einen Dienst namens . Das von Ihrem VSPackage erstellte Objekt, das im `QueryService` Fensterrahmen eingerichtet wurde, <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> muss die Methode aufrufen, um einen Zeiger auf die Schnittstelle abzurufen.

 Rahmenfenster können verhindern, dass Teile ihrer Auswahlkontextinformationen beim Starten an den globalen Auswahlkontext weitergegeben werden. Diese Fähigkeit ist nützlich für Toolfenster, die möglicherweise mit einer leeren Auswahl beginnen müssen.

 Durch Ändern des globalen Auswahlkontexts werden Ereignisse ausgelöst, die VSPackages überwachen kann. VSPackages kann die folgenden `IVsTrackSelectionEx` Aufgaben <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> ausführen, indem es implementiert und Schnittstellen bereitstellt:

- Aktualisieren Sie die aktuell aktive Datei in einer Hierarchie.

- Überwachen Sie Änderungen an bestimmten Elementtypen. Wenn Ihr VSPackage beispielsweise ein spezielles **Eigenschaftenfenster** verwendet, können Sie Änderungen im aktiven **Eigenschaftenfenster** überwachen und Ihre bei Bedarf neu starten.

  Die folgende Sequenz zeigt den typischen Verlauf der Auswahlverfolgung.

1. Die IDE ruft den Auswahlkontext aus dem neu geöffneten Fenster ab und fügt ihn in den globalen Auswahlkontext ein. Wenn der Auswahlkontext HIERARCHY_DONTPROPAGATE oder SELCONTAINER_DONTPROPAGATE verwendet, werden diese Informationen nicht an den globalen Kontext weitergegeben. Weitere Informationen finden Sie unter [Feedback an den Benutzer](../../extensibility/internals/feedback-to-the-user.md).

2. Benachrichtigungsereignisse werden an jedes VSPackage übertragen, das sie angefordert hat.

3. Das VSPackage wirkt auf die Empfangen von Ereignissen, indem es Aktivitäten wie das Aktualisieren einer Hierarchie, das Reaktivieren eines Werkzeugs oder andere ähnliche Aufgaben ausführt.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Auswahl und Aktualität in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Projekttypen](../../extensibility/internals/project-types.md)
