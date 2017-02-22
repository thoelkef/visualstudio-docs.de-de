---
title: "Text-Puffer-Ereignisse in der Legacy-API | Microsoft Docs"
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
  - "Editoren [Visual Studio SDK] legacy - Puffer Ereignisse"
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# Text-Puffer-Ereignisse in der Legacy-API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Textpuffer Objekt gibt verschiedene Ereignisse aus, die es Ihnen ermöglichen, um unterschiedlichen Situationen zu begegnen.  
  
 Wenn Sie das Legacy APIs verwenden, sollten Sie die folgenden Schnittstellen implementieren, um Benachrichtigungen über Änderungen am Textpuffer zu empfangen.  Setzen Sie die Schnittstellen im Textpuffer mithilfe der `IConnectionPointContainer`\-Schnittstelle im Textpuffer aus, um Benachrichtigungen über Zzeilenwechseln aus dem Puffer zu empfangen.  Weitere Informationen finden Sie unter [Gewusst wie: Registrieren für Ereignisse Puffer mit der Legacy\-API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md).  Im Fall `IVsTextStreamEvents` oder `IVsTextLinesEvents`\-Schnittstellen werden Änderungen in ein oder zweidimensionalen Koordinaten zurückgegeben werden.  
  
## Simsen Sie Puffer\-Schnittstellen  
 Im Folgenden werden die Schnittstellen, die vom Textpuffer Objekt implementiert sind.  
  
|Schnittstelle|Beschreibung|  
|-------------------|------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Aktiviert die Erstellung von zusammengesetzten Aktionen \(das heißt Aktionen, die in einem einzelnen Rückgängig\/Wiederholen\-Gerät gruppiert\).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Aktiviert die Beibehaltung von Dokumenten von Daten, die von den Textpuffer verwaltet werden.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Stellt Basisdienste. Verwendung durch viele Clients.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Stellt Funktionen bereit, Lese\- und Schreibvorgänge anhand der zweidimensionalen Koordinaten.  Erbt von `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Erstellt schnellen, Datenstrom\-ausgerichtet, sequenzieller Zugriff auf den Text im Puffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Stellt Funktionen bereit, Lese\- und Schreibvorgänge anhand der eindimensionales Koordinaten.  Erbt von `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Bietet Zugriff auf einer generischen Auflistung von Eigenschaften.  Die wichtigste Eigenschaft ist der Name des Puffers Moniker oder legt diese fest.  Sie können speichern, Zufallsdaten im Puffer dieser Schnittstelle verfügen, indem Sie ein GUID erstellen und dann als Schlüssel verwenden.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Unterstützt Verbindungspunkte für Ereignisse.|  
  
## Text\-Puffer\-Ereignisschnittstellen  
 Im Folgenden werden die Schnittstellen für Text puffer\-Ereignis Ereignisbenachrichtigung.  
  
|Schnittstelle|Beschreibung|  
|-------------------|------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Benachrichtigt Clients, wenn ein neuer Sprachdienst mit einem Textpuffer zugeordnet ist.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Benachrichtigt Clients, wenn kein Textpuffer initialisiert wird und wenn Änderungen an den Daten im Textpuffer vorgenommen werden.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Benachrichtigt Clients über Änderungen am zugrunde liegenden Textpuffer im eindimensionalen Koordinaten.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Benachrichtigt Clients über Änderungen am zugrunde liegenden Textpuffer im zweidimensionalen Koordinaten.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Benachrichtigt Clients über Änderungen an Benutzerdaten.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Benachrichtigt Clients über der letzten Commit geste, um das Ereignis auszulösen und stellt den Textbereich geändert.  Die `IVsPreliminaryTextChangeCommitEvents`\-Schnittstelle wird nicht als Antwort auf rückgängig machen oder wiederholen Befehle ausgelöst.  lösen Ereignisse aus, die nur für Puffer Rückgängig einen Manager haben.  `IVsPreliminaryTextChangeCommitEvents` wird vor anderen Ereignissen, wie hübschen Listen ausgelöst, um sich anderen Ereignisse mit Text nicht sicher ändern, bevor die Änderungen übernommen werden.  VSPackage muss entweder die `IVsPreliminaryTextChangeCommitEvents`\-Schnittstelle oder die `IVsFinalTextChangeCommitEvents`\-Schnittstelle, jedoch nicht beides überwacht werden.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Benachrichtigt Clients über der letzten Commit geste, um das Ereignis auszulösen und stellt den Textbereich geändert.  Die `IVsFinalTextChangeCommitEvents`\-Schnittstelle wird nicht als Antwort auf rückgängig machen oder wiederholen Befehle ausgelöst.  lösen Ereignisse aus, die nur für Puffer Rückgängig einen Manager haben.  `IVsFinalTextChangeCommitEvents` ist nur für die Verwendung durch Sprachendienste oder andere Objekte bestimmt, die vollständige Kontrolle über bearbeiten.  VSPackage muss entweder die `IVsPreliminaryTextChangeCommitEvents`\-Schnittstelle oder die `IVsFinalTextChangeCommitEvents`\-Schnittstelle, jedoch nicht beides überwacht werden.|  
  
## Siehe auch  
 [Zugriff auf den Textpuffer mit der Legacy\-API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Gewusst wie: Registrieren für Ereignisse Puffer mit der Legacy\-API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)