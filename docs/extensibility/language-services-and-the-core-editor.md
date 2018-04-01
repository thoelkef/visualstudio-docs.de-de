---
title: Language-Dienste und die Core-Editor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c3d2bcad21bb919125b487a57b73d3a458a3a1f9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="language-services-and-the-core-editor"></a>Language-Dienste und die Core-Editor
In Visual Studio-Editoren sind häufig einen Sprachdienst zugeordnet. Unter anderem bietet ein Sprachdienst Syntaxfarben, Anweisungsvervollständigung, IntelliSense und Formatieren von Text.  
  
## <a name="core-editors-and-document-data-objects"></a>Core-Editoren und Data-Dokumentobjekte  
 Wenn Sie den Core-Editor zuzugreifen, erstellt nicht der Dokumentdaten und Ansicht-Dokumentobjekte. Die IDE erstellt und steuert diese zwei Objekte, und Abrufen von Handles für diese durch Aufrufe der entsprechenden im Editor Factory-Implementierung.  
  
 Weitere Informationen finden Sie unter [bestimmen den Editor öffnet eine Datei in einem Projekt](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Language-Dienste und die Core-Editor  
 Durch implementieren einen Sprachdienst, können Sie steuern, wie Daten in der Dokumentansicht angezeigt werden. Ein Sprachdienst enthält Informationen und Verhalten, das für eine bestimmte Sprache, z. B. Visual C++ spezifisch sind. Beim Erstellen eines Textpuffers und bestimmen die Dateierweiterung für das Dokument, das Sie öffnen, bestimmt der Textpuffer der Sprachdienst diese Name-Dateierweiterung aus einem Registrierungsschlüssel HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors zugeordnet \\\Extensions {YourLanguageService GUID}. Laden die Prozedur dann standard VSPackage lädt das VSPackage und eine Instanz des Sprachdiensts erstellt.  
  
 Ein grundlegende Sprachdienst ist in der folgenden Abbildung gezeigt.  
  
 ![Sprachdienstmodell](../extensibility/media/vslanguageservicemodel.gif "VsLanguageServiceModel")  
Core-Editor und Language Service-Objekten  
  
 Das Dokument-Datenobjekt für den Core-Editor ist einen Textpuffer aufgerufen und wird durch die <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt. Das Ansichtsobjekt Dokument wird eine Textansicht aufgerufen und wird durch die <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> Objekt. Diesen beiden Objekten arbeiten zusammen, bis der Sprachdienst ermöglichen einen schnellen Überblick über die Core-Editor. Informationen aus den Textpuffer und zeigt den Text in einem Dokumentfenster wird ein Codefenster aufgerufen. Das Code-Fenster-Dokument wird von einem Code-Fenster-Manager verwaltet.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Bereitstellen von Language Dienstkontext über die Legacy-API](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Hosten von IntelliSense](../extensibility/intellisense-hosting.md)   
 [Enthaltenen Sprachen](../extensibility/contained-languages.md)   
 [Entwickeln eines Legacysprachdiensts](../extensibility/internals/developing-a-legacy-language-service.md)