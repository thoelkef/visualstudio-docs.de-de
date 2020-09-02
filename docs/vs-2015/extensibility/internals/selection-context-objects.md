---
title: Auswahl Kontext Objekte | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e1a43997d56f8d89f194fb83d20c1f160378873
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187430"
---
# <a name="selection-context-objects"></a>Auswahlkontextobjekte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) verwendet ein globales Auswahl Kontext Objekt, um zu bestimmen, was in der IDE angezeigt werden soll. Für jedes Fenster in der IDE kann ein eigenes Auswahl Kontext Objekt in den globalen Auswahl Kontext übermittelt werden. Die IDE aktualisiert den globalen Auswahl Kontext mit Werten aus einem Fenster, wenn dieses Fenster den Fokus besitzt. Weitere Informationen finden Sie unter [Feedback an den Benutzer](../../extensibility/internals/feedback-to-the-user.md).  
  
 Jeder Fensterrahmen oder jede Site in der IDE verfügt über einen Dienst mit dem Namen <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . Das von Ihrem VSPackage erstellte Objekt, das im Fensterrahmen positioniert ist, muss die- `QueryService` Methode aufzurufen, um einen Zeiger auf die- <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> Schnittstelle zu erhalten.  
  
 Rahmen Fenster können Teile Ihrer Auswahl Kontextinformationen daran halten, beim Start an den globalen Auswahl Kontext weitergegeben zu werden. Diese Fähigkeit ist nützlich für Tool Fenster, die möglicherweise mit einer leeren Auswahl beginnen müssen.  
  
 Durch das Ändern des globalen Auswahl Kontexts werden Ereignisse ausgelöst, die von VSPackages überwacht werden können. VSPackages können die folgenden Aufgaben durch Implementieren von `IVsTrackSelectionEx` -und- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> Schnittstellen ausführen:  
  
- Aktualisieren Sie die derzeit aktive Datei in einer Hierarchie.  
  
- Überwachen von Änderungen an bestimmten Elementtypen. Wenn für Ihr VSPackage beispielsweise ein spezielles **Eigenschaften** Fenster verwendet wird, können Sie Änderungen im aktiven **Eigenschaften** Fenster Überwachen und bei Bedarf ihren Neustart starten.  
  
  Die folgende Sequenz zeigt den typischen Verlauf der Auswahl Nachverfolgung.  
  
1. Die IDE Ruft den Auswahl Kontext aus dem neu geöffneten Fenster ab und legt ihn im globalen Auswahl Kontext ab. Wenn der Auswahl Kontext HIERARCHY_DONTPROPAGATE oder SELCONTAINER_DONTPROPAGATE verwendet, werden diese Informationen nicht an den globalen Kontext weitergegeben. Weitere Informationen finden Sie unter [Feedback an den Benutzer](../../extensibility/internals/feedback-to-the-user.md).  
  
2. Benachrichtigungs Ereignisse werden an jedes VSPackage gesendet, das Sie angefordert hat.  
  
3. Das VSPackage wirkt sich auf die empfangenen Ereignisse aus, indem er Aktivitäten wie das Aktualisieren einer Hierarchie, das erneute Aktivieren eines Tools oder andere ähnliche Aufgaben ausführt.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Auswahl und Währung in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Projekttypen](../../extensibility/internals/project-types.md)
