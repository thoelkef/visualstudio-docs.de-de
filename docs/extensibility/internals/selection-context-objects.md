---
title: "Auswahl Kontextobjekte | Microsoft Docs"
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
  - "Auswahl und Nachverfolgen"
  - "Auswahl Kontextobjekte"
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Auswahl Kontextobjekte
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung \(IDE\) verwendet ein globales Auswahlkontext, um zu bestimmen, was in der IDE angezeigt werden soll.  Jedes Fenster in der IDE kann ihr eigenes Auswahlkontext Objekt verfügen, das auf den globalen Auswahlkontext gedrückt wird.  Die IDE aktualisiert den globalen Auswahlkontext mit Werten aus einem Fenster, wenn dieses Fenster den Fokus besitzt.  Weitere Informationen finden Sie unter [Feedback an den Benutzer](../../extensibility/internals/feedback-to-the-user.md).  
  
 Jeder Fensterrahmen oder Website in der IDE hat einen Dienst, der <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>aufgerufen wird.  Das Objekt, das von einem VSPackage erstellt wird, das im Fensterrahmen positioniert ist, muss die `QueryService`\-Methode aufrufen, um einen Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>\-Schnittstelle abzurufen.  
  
 Rahmenfenster können Teile ihrer Auswahl von Kontextinformationen zur Auswahlkontext auf den globalen weitergegeben werden, wenn sie gestartet werden.  Diese Fähigkeit ist nützlich für Toolfenster, die mit einer leeren Auswahl beginnen müssen.  
  
 Das Ändern des globalen Auswahl kontexts löst Ereignisse, die VSPackages überwachen kann.  VSPackages kann die folgenden Aufgaben ausführen, indem `IVsTrackSelectionEx` und <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>\-Schnittstellen implementiert:  
  
-   Aktualisieren Sie die aktuell aktive Datei in einer Hierarchie.  
  
-   Überwachen von Änderungen an bestimmten Elementtypen.  Wenn beispielsweise ein VSPackage ein spezielles **Eigenschaften** Fenster verwendet, können Sie Änderungen im aktiven **Eigenschaften** Fenster Überwachen und thes nach Bedarf neu starten.  
  
 Die folgende Sequenz wird die typische Kurs der Auswahl nachverfolgung an.  
  
1.  Die IDE ruft den Auswahlkontext aus dem neu geöffneten Fenster ab und setzt sie in den globalen Auswahlkontext ein.  Wenn der Auswahlkontext HIERARCHY\_DONTPROPAGATE oder SELCONTAINER\_DONTPROPAGATE verwendet, werden diese Informationen nicht in den globalen Kontext weitergegeben.  Weitere Informationen finden Sie unter [Feedback an den Benutzer](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  Benachrichtigungsereignisse sind für jeden VSPackage übertragen, das sie angefordert hat.  
  
3.  VSPackage wird Ereignissen, die diese empfängt, indem Aktivitäten wie die Aktualisierung einer Hierarchie oder einem Tool erneut ausführen und andere ähnliche Aufgaben.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Auswahl und Währung, in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Projekttypen](../../extensibility/internals/project-types.md)