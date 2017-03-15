---
title: "Language Services und die Core-Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - Language services"
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Language Services und die Core-Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Editoren in Visual Studio werden oft mit einem Sprachdienst zugeordnet.  Unter anderem stellt ein Sprachdienst Syntaxfarbe, Anweisungsvervollständigung, IntelliSense und Textformatierung bereit.  
  
## Kern\-Editoren und Dokumenten\-Datenobjekte  
 Wenn Sie den Kern des Editors zugreifen, erstellen Sie nicht die Objekte und Dokumenten Dokumentdaten.  Die IDE erstellt und steuert diese beiden Objekte, und Sie erhalten Handles darauf, indem Sie die entsprechenden Aufrufe in der Implementierung des Editors factory machen.  
  
 Weitere Informationen finden Sie unter [Bestimmen daraufhin\-Editor eine Datei in einem Projekt](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## Sprachendienste und der Kern\-Editor  
 Wenn Sie einen Sprachdienst implementieren, können Sie steuern, wie Daten in der Ansicht Dokumente angezeigt wird.  Ein Sprachdienst, das Verhalten und stellt Informationen zu einer bestimmten Sprache bestimmt wird, wie Visual C\+\+.  Wenn Sie einen Textpuffer erstellen und die Dateinamenerweiterung für das Dokument öffnen, das bestimmt, bestimmt der Sprachdienst den Textpuffer, der mit der Dateinamenerweiterung von einem Registrierungsschlüssel HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ Editoren \\ zugeordnet ist TheLanguageService {GUID} \\ Extensions.  Standard\-VSPackage, das Verfahren lädt und VSPackages geladen, dann eine Instanz des Sprachdiensts wird erstellt.  
  
 Ein grundlegender Sprachdienst wird in der folgenden Abbildung dargestellt.  
  
 ![Grafik zum Sprachdienstmodell](../extensibility/media/vslanguageservicemodel.png "vsLanguageServiceModel")  
Kern des Editors und Sprachdienst Objekte  
  
 Das Dokument wird das angegebene Channeldatenobjekt für den Kern des Editors einen Textpuffer bezeichnet und wird durch das <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>\-Objekt dargestellt.  Das Objekt der Dokumente ist eine Textansicht bezeichnet und wird durch das <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>\-Objekt dargestellt.  Diese beiden Objekte funktionieren vom Sprachdienst zusammen, um eine einheitliche Ansicht des zentralen editors bereitzustellen.  Informationen im Textpuffer und den Text anzeigen, der in einem Dokumentfenster namens ein Codefenster an.  Das Codefenster Dokument wird von einem Code fenster\-manager verwaltet.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Bietet einen Dienstkontext Sprache mit der Legacy\-API](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Hosten von IntelliSense](../extensibility/intellisense-hosting.md)   
 [Enthaltene Sprachen](../extensibility/contained-languages.md)   
 [Entwickeln einer Sprache](../extensibility/internals/developing-a-legacy-language-service.md)