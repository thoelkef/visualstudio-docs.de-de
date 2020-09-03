---
title: Sprachdienste und der Kern-Editor | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e708ffe796bfc9342bc20c3e7f20d5cf0d05058
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180306"
---
# <a name="language-services-and-the-core-editor"></a>Sprachdienste und der Core-Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editoren in Visual Studio sind häufig einem Sprachdienst zugeordnet. Unter anderem bietet ein Sprachdienst Syntax Farben, Anweisungs Vervollständigung, IntelliSense und Textformatierung.  
  
## <a name="core-editors-and-document-data-objects"></a>Kern-Editoren und Dokument Datenobjekte  
 Wenn Sie auf den Kern-Editor zugreifen, erstellen Sie keine Dokument Daten und Dokument Ansichts Objekte. Die IDE erstellt und steuert diese beiden Objekte, und Sie erhalten Handles, indem Sie die entsprechenden Aufrufe in der Editorfactory-Implementierung vornehmen.  
  
 Weitere Informationen finden Sie unter [bestimmen, welcher Editor eine Datei in einem Projekt öffnet](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Sprachdienste und der Core-Editor  
 Durch Implementieren eines sprach Dienstanbieter können Sie steuern, wie Daten in der Dokument Ansicht angezeigt werden. Ein Sprachdienst stellt Informationen und Verhaltensweisen bereit, die für eine bestimmte Sprache spezifisch sind, z. b. Visual C++. Wenn Sie einen Text Puffer erstellen und die Dateinamenerweiterung für das Dokument ermitteln, das Sie öffnen, bestimmt der Text Puffer den Sprachdienst, der dieser Dateinamenerweiterung von einem Registrierungsschlüssel zugeordnet ist, HKEY_LOCAL_MACHINE \software\microsoft\editoren \\ {yourlanguageservice GUID} \extensions. Die standardmäßige VSPackage-Lade Prozedur lädt dann das VSPackage, und eine Instanz Ihres sprach Dienstanbieter wird erstellt.  
  
 Ein grundlegender Sprachdienst wird in der folgenden Abbildung dargestellt.  
  
 ![Grafik zum Sprachdienstmodell](../extensibility/media/vslanguageservicemodel.gif "vslanguageservicemodel")  
Kern-Editor und Sprachdienst Objekte  
  
 Das Dokument Datenobjekt für den Kern-Editor wird als Text Puffer bezeichnet und durch das- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt dargestellt. Das Dokument Ansichts Objekt wird als Textansicht bezeichnet und wird durch das- <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> Objekt dargestellt. Diese beiden Objekte arbeiten über den Sprachdienst zusammen, um eine einheitliche Ansicht des Kern Editors bereitzustellen. Informationen aus dem Text Puffer und der Textansicht werden in einem Dokument Fenster angezeigt, das als Code Fenster bezeichnet wird. Das Code Fenster Dokument wird von einem Code Fenster-Manager verwaltet.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Bereitstellen eines Sprachdienst Kontexts mithilfe der Legacy-API](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [IntelliSense-Hosting](../extensibility/intellisense-hosting.md)   
 [Enthaltene Sprachen](../extensibility/contained-languages.md)   
 [Entwickeln eines Legacysprachdiensts](../extensibility/internals/developing-a-legacy-language-service.md)
