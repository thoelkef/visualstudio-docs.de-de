---
title: -Editor, und Language Service Extensions | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 67d250a2806b367a76fa593026f10d4b671c21b2
ms.lasthandoff: 02/22/2017

---
# <a name="editor-and-language-service-extensions"></a>-Editor, und Language Service Extensions
Sie können die meisten Funktionen des Code-Editor von Visual Studio erweitern. Der Editor basiert auf Windows Presentation Foundation (WPF) und in verwaltetem Code geschrieben wird. Obwohl dadurch die Entwürfe in früheren Versionen von Visual Studio unterscheidet, bereitgestellt größtenteils die gleichen Funktionen. Verwenden Sie zum Erweitern des Editors das Managed Extensibility Framework (MEF).  
  
 Das Visual Studio SDK stellt Adapter, die genannte *Shims* VSPackages zu unterstützen, die für frühere Versionen geschrieben wurden. Dennoch, wenn Sie eine vorhandene VSPackage haben, wird empfohlen, dass die Aktualisierung auf die neue Technologie, um eine bessere Leistung und Zuverlässigkeit zu erhalten.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Erstellen eine Erweiterung mit einer Elementvorlage-Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Einführung in die Editor-Elementvorlagen.|  
|[Erweitern der-Editor und Sprachdienste](../extensibility/extending-the-editor-and-language-services.md)|Links zu Dokumenten, die Einführung der Entwurf und die Funktionen des Editors Core und zeigen, wie Sie es erweitern.|  
|[Legacy-Schnittstellen im Editor](../extensibility/legacy-interfaces-in-the-editor.md)|Enthält Links zu Dokumenten, die erläutert, wie den Core-Editor aus vorhandenem Code zugreifen.|  
|[Erstellen von benutzerdefinierten Editoren und Designern](../extensibility/creating-custom-editors-and-designers.md)|Links zu Dokumenten, die erklären, wie benutzerdefinierte Editoren erstellt.|  
|[Ältere Sprache Service-Erweiterbarkeit](../extensibility/internals/legacy-language-service-extensibility.md)|Links zu Dokumenten, die beschreiben, wie Sie Programmiersprachen in Visual Studio integrieren.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Führt das Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Führt die Windows Presentation Foundation (WPF).|
