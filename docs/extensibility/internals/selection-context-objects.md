---
title: Auswahl Kontextobjekte | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 04ccc4a57ac7af144c134761119433b7533e9bec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131260"
---
# <a name="selection-context-objects"></a>Auswahl Kontextobjekte
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE) verwendet ein Kontextobjekt für die globale Auswahl, um zu bestimmen, was in der IDE angezeigt werden soll. Jedes Fenster in der IDE kann eigene Auswahl Context-Objekt an den Kontext der globalen Auswahl abgelegt haben. Die IDE aktualisiert den globalen Auswahlkontext mit Werten aus einem Fenster, wenn das Fenster den Fokus besitzt. Weitere Informationen finden Sie unter [Feedback an den Benutzer](../../extensibility/internals/feedback-to-the-user.md).  
  
 Jeder Fensterrahmen oder Website in der IDE verfügt über einen Dienst namens <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Das Objekt erstellt, indem das VSPackage, die in der Fensterrahmen positioniert wird aufrufen muss die `QueryService` Methode, um einen Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> Schnittstelle.  
  
 Rahmenfenster können Teile ihrer Auswahl Kontextinformationen von an den Kontext der globalen Auswahl weitergegeben werden, wenn sie gestartet werden beibehalten. Diese Fähigkeit ist nützlich für Toolfenster, die mit einer leeren Auswahl beginnen können.  
  
 Ändern der globalen Auswahl Kontext löst Ereignisse, die VSPackages überwachen können. VSPackages können die folgenden Aufgaben ausführen, durch die Implementierung `IVsTrackSelectionEx` und <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> Schnittstellen:  
  
-   Aktualisieren Sie die gerade aktive Datei in einer Hierarchie.  
  
-   Überwachen Sie Änderungen an bestimmten Arten von Elementen. Wenn Ihr VSPackage ein spezielles verwendet z. B. **Eigenschaften** Fenster können Sie Änderungen im aktiven Überwachen **Eigenschaften** Fenster und neu starten, wenn erforderlich.  
  
 Die folgende Sequenz veranschaulicht des normalen Betriebs auswahlnachverfolgung.  
  
1.  Die IDE Ruft den Auswahlkontext aus dem neu geöffneten Fensters ab und fügt sie in den Kontext der globalen Auswahl. Wenn die Auswahlkontext HIERARCHY_DONTPROPAGATE oder SELCONTAINER_DONTPROPAGATE verwendet, wird diese Informationen nicht an den globalen Kontext weitergegeben. Weitere Informationen finden Sie unter [Feedback an den Benutzer](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  Benachrichtigungsereignisse werden an alle VSPackage übermittelt, die sie angefordert hat.  
  
3.  Das VSPackage, auf die Ereignisse, die es empfängt, durch Ausführen von Aktivitäten wie das Aktualisieren von einer Hierarchie, und reaktivieren ein Tool oder andere ähnlichen Aufgaben fungiert.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Auswahl und Währung, in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Projekttypen](../../extensibility/internals/project-types.md)