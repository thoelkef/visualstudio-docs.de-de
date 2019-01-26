---
title: Sprachdienste und die Kern-Editor | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21785e7aed4e59e9ee7852bdb5474f7c1ca9d95f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031733"
---
# <a name="language-services-and-the-core-editor"></a>Sprachdienste und die Kern-editor
Editoren von Visual Studio werden häufig von einem Sprachdienst zugeordnet. Unter anderem bietet ein Sprachdienst, farbige syntaxmarkierung, Anweisungsvervollständigung, IntelliSense und textformatierung.  
  
## <a name="core-editors-and-document-data-objects"></a>Core-Editoren und dokumentdatenobjekten  
 Wenn Sie die Kern-Editor zuzugreifen, Sie Dokumentdaten und dokumentenansichtsobjekten nicht erstellen. Die IDE erstellt und diesen beiden Objekten steuert, und Sie verarbeitet werden, indem Sie die entsprechenden Aufrufe in Ihrem Editor Factoryimplementierung machen abrufen.  
  
 Weitere Informationen finden Sie unter [zu bestimmen, welcher Editor eine Datei in einem Projekt öffnet](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Sprachdienste und die Kern-editor  
 Implementieren Sie einen Sprachdienst, können Sie steuern, wie Daten in der Dokumentenansicht angezeigt werden. Ein Sprachdienst, bietet Informationen und Verhaltensweisen, die für eine bestimmte Sprache, z. B. Visual C++ spezifisch sind. Wenn Sie einen Textpuffer zu erstellen und ermitteln die Dateierweiterung für das Dokument, das Sie öffnen, bestimmt der Textpuffer den Sprachdienst diese Dateinamenerweiterung aus einem Registrierungsschlüssel zugeordnet **HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\Editors\\{YourLanguageService GUID} \Extensions**. Laden die Prozedur dann standard VSPackage lädt das VSPackage, und eine Instanz des Sprachdiensts wird erstellt.  
  
 Ein einfachen Sprachdiensts wird in der folgenden Abbildung angezeigt.  
  
 ![Sprachdienstmodell](../extensibility/media/vslanguageservicemodel.gif "VsLanguageServiceModel")  
Core-Editoren und Sprachen Dienstobjekte  
  
 Das dokumentendatenobjekt für die Kern-Editor wird aufgerufen, einen Textpuffer und wird durch die <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt. Das dokumentenansichtsobjekt eine Textansicht aufgerufen wird, und wird durch die <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> Objekt. Diese beiden Objekte arbeiten zusammen, über den Sprachdienst einen einheitlichen Überblick über die Kern-Editor angeben. Informationen aus dem Textpuffer und zeigt den Text in einem Dokumentfenster wird ein Code-Fenster aufgerufen. Das Dokument der Code-Fenster wird durch einen Codefenster-Manager verwaltet.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Geben Sie einen Dienstkontext für die Sprache mit der legacy-API](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Hosten von IntelliSense](../extensibility/intellisense-hosting.md)   
 [Enthaltene Sprachen](../extensibility/contained-languages.md)   
 [Entwickeln eines Datendiensts legacysprache](../extensibility/internals/developing-a-legacy-language-service.md)