---
title: "MSBuild-Fehler MSB8031 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSB8031"
ms.assetid: ebfaca51-fd91-4b04-8194-b4fdededd5fe
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild-Fehler MSB8031
MSB8031  
  
 Um die MBCS\-Codierung in MFC\-Projekten zu verwenden, müssen Sie eine zusätzliche Bibliothek herunterladen und installieren.  
  
 MBCS\-Versionen der MFC\-DLLs sind nicht in Visual Studio enthalten, aber sie sind im MFC MBCS DLL\-Add\-On verfügbar, das Sie herunterladen können, wenn Sie ein Visual Studio\-Kunde sind.  Wenn Sie das Add\-On nicht installieren und versuchen, ein MFC\-Projekt zu erstellen, das den MBCS\-Zeichensatz verwendet, findet der Linker die DLLs nicht, und der Build schlägt fehl.  
  
### So beheben Sie diesen Fehler  
  
1.  [Laden Sie das MBCS MFC DLL\-Add\-On](http://go.microsoft.com/fwlink/?LinkId=299009) vom MSDN\-Downloadcenter herunter, oder konvertieren Sie ggf. Ihr Projekt in den Unicode\-Zeichensatz, falls sich dies anbietet.  
  
## Siehe auch  
 [MFC MBCS DLL\-Add\-On](/visual-cpp/mfc/mfc-mbcs-dll-add-on)