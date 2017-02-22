---
title: "Zugreifen auf Dietext Ansicht mithilfe der Legacy-API | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - Ansicht"
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Zugreifen auf Dietext Ansicht mithilfe der Legacy-API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine Textansicht ist eine Darstellung von Text, der in einem Textpuffer gespeichert wird.  Sie können die Textansicht zugreifen, indem Sie das Legacy APIs wie im folgenden Abschnitt gezeigt.  
  
## Text\-Ansichts\-Objekt  
 Jede Ansicht wird mit seinem eigenen Textpuffer zugeordnet, und die Ansicht handelt es sich um ein Fenster auf die Daten im Puffer.  Das folgende Diagramm zeigt die wichtigsten Schnittstellen der Text des Objekts an, das von <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>dargestellt wird.  
  
 ![Visual Studio&#45;TextView&#45;Objekt](../extensibility/media/vstextview.png "vstextview")  
Text für die  
  
 Die Ansicht ist eine Methode des Vorlegens des Texts im Puffer.  Sie schließt Funktionen wie Zeilenumbruch und Gliederungen, damit ein, was Sie in der Ansicht finden, keine genaue Darstellung des Texts im Puffer ist.  
  
 Eine Ansicht können andere Dienste oder Prozessen, um eingehende Befehle nach abzufangen und zu behandeln, bevor die Ansicht hinter ihnen angewendet wird.  Die häufigste Dienst, um hierzu ein Sprachdienst.  Ein Sprachdienst erfordern, z. B. finge möglicherweise den Befehl ab, sodass die EINGABETASTE benutzerdefiniertes Verhalten des Einzugs oder QuickInfos bereitstellt.  
  
## Funktionen hinzufügen Text\-Ansicht  
 Sie können das Verhalten der Text anpassen, indem Sie bestimmte Tastatureingaben behandeln.  Um die Tastatureingaben abzufangen, implementieren Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> auf das Objekt, und erstellen ein Befehlsziel \(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\) um Befehle zu überwachen und abzufangen.  
  
 Die Textansicht verwendet sequenzielle Architektur für Filter Befehls.  Filter \(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Befehls Neue Objekte\) werden in der Reihenfolge hinzugefügt, indem die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>\-Methode aufgerufen wird.  
  
 Ereignisbenachrichtigungen für die Textansicht wird von der Verwendung der `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents`\-Schnittstelle bereitgestellt.  Implementieren Sie diese Schnittstelle für das Clientobjekt, um Benachrichtigungen über Änderungen an der Textansicht zu empfangen.  Legen Sie diese Schnittstelle der Textansicht aus, indem Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>\-Schnittstelle für die Textansicht verwenden, um Benachrichtigungen über Änderungen aus der Ansicht zu empfangen.  
  
## Siehe auch  
 [Ändern die Ansicht mit der Legacy\-API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Verwenden die Text\-Manager zum Überwachen von globaler Einstellungen](../extensibility/using-the-text-manager-to-monitor-global-settings.md)