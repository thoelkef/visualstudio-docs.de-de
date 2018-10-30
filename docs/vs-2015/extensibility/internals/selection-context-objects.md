---
title: Auswahlkontextobjekte | Microsoft-Dokumentation
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
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b3d65a1fb510daec68060261141ddb2d05822988
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836852"
---
# <a name="selection-context-objects"></a>Auswahlkontextobjekte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (IDE) verwendet ein Kontextobjekt für die globale Auswahl, um zu bestimmen, was in der IDE angezeigt werden soll. Jedes Fenster in der IDE haben eine eigene per Push an den globalen Auswahlkontext Auswahl Context-Objekt. Die IDE aktualisiert den Kontext für die globale Auswahl mit Werten aus einem Fenster, wenn das Fenster den Fokus hat. Weitere Informationen finden Sie unter [Feedback an den Benutzer](../../extensibility/internals/feedback-to-the-user.md).  
  
 Jeder Fensterrahmen oder der Standort in der IDE verfügt über einen Dienst namens <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Aufrufen des Objekts, das von einem VSPackage, das im Fensterrahmen positioniert wird erstellt, muss die `QueryService` -Methode zum Abrufen der eines Zeigers auf die <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> Schnittstelle.  
  
 Rahmenfenster können Teile ihrer Auswahl Kontextinformationen aus an den globalen Auswahlkontext weitergegeben wird, wenn sie gestartet wurden, beibehalten. Diese Möglichkeit eignet sich für die Toolfenster, die mit der eine leere Auswahl beginnen können.  
  
 Ändern die globale Auswahl Kontext löst Ereignisse, die VSPackages überwachen können. VSPackages können die folgenden Aufgaben ausführen, durch die Implementierung `IVsTrackSelectionEx` und <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> Schnittstellen:  
  
- Aktualisieren Sie die aktive Datei in einer Hierarchie.  
  
- Überwachen von Änderungen an, um bestimmte Arten von Elementen. Wenn das VSPackage einen speziellen verwendet z. B. **Eigenschaften** Fenster können Sie Änderungen an das aktive Überwachen **Eigenschaften** Fenster und Ihnen bei Bedarf neu zu starten.  
  
  Die folgende Sequenz zeigt die typische Vorgehensweise auswahlnachverfolgung.  
  
1.  Die IDE den Auswahlkontext aus des neu geöffneten Fensters abgerufen und in den globalen Auswahlkontext eingefügt. Wenn die Auswahlkontext HIERARCHY_DONTPROPAGATE oder SELCONTAINER_DONTPROPAGATE verwendet, wird diese Informationen nicht an den globalen Kontext weitergegeben. Weitere Informationen finden Sie unter [Feedback an den Benutzer](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  Benachrichtigungsereignisse sind an jedem VSPackage übertragen, die sie angefordert hat.  
  
3.  Das VSPackage fungiert, auf die Ereignisse, die es empfängt, indem Sie Aktivitäten wie das Aktualisieren einer Hierarchie, und reaktivieren ein Tool oder andere ähnlichen Aufgaben ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Auswahl und Aktualität in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Projekttypen](../../extensibility/internals/project-types.md)

