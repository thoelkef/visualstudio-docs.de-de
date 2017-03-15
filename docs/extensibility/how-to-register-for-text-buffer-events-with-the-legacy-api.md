---
title: "Gewusst wie: Registrieren f&#252;r Ereignisse Puffer mit der Legacy-API | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - registrieren Text-Puffer-Ereignisse"
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Gewusst wie: Registrieren f&#252;r Ereignisse Puffer mit der Legacy-API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie den Textpuffer zugreifen, indem Sie das Legacy APIs verwenden, sollten Sie für Textpuffer Ereignisse wie in der folgenden Prozedur gezeigt registrieren.  
  
### So Textpuffer Events anmelden  
  
1.  Aus einem Zeiger auf eine der Schnittstellen für <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, rufen Sie `QueryInterface` für einen Zeiger auf <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>\-Methode auf, und übergeben Sie die Schnittstellen\-ID der Ereignisse, für die Sie registrieren möchten.  
  
     Wenn Sie beispielsweise für <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>registrieren möchten, übergeben Sie IID\_IVsTextLinesEvents der Schnittstellen\-ID.  
  
     Der Textpuffer gibt einen Zeiger auf die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>\-Schnittstelle für das entsprechende Verbindungspunktobjekt zurück.  
  
3.  Mithilfe des Zeigers rufen Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>\-Methode aufrufen und einen Zeiger auf die Implementierung der Schnittstelle Ereignis übergeben, für die Sie zum Beispiel die `IVsTextLinesEvents`\-Schnittstelle registrieren möchten.  
  
     Die Umgebung wird ein Cookie zurück, das Sie verwenden können, um Ereignisse zu überwachen, zu beenden, indem Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>\-Methode aufrufen.  
  
## Siehe auch  
 [Text\-Puffer\-Ereignisse in der Legacy\-API](../extensibility/text-buffer-events-in-the-legacy-api.md)