---
title: Editor-und Sprachdienst Erweiterungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7fa3e4be6ee44011eb1286e3ebf22ee69f8e3397
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683115"
---
# <a name="editor-and-language-service-extensions"></a>Editor- und Sprachdiensterweiterungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die meisten Features von Visual Studio Code-Editor können erweitert werden. Der Editor basiert auf dem Windows Presentation Foundation (WPF) und wird in verwaltetem Code geschrieben. Obwohl dieser Entwurf sich von den Entwürfen in früheren Versionen von Visual Studio unterscheidet, bietet er die meisten der gleichen Funktionen. Um den Editor zu erweitern, verwenden Sie den Managed Extensibility Framework (MEF).  
  
 Das Visual Studio SDK bietet Adapter, die als *Shims* bezeichnet werden, um VSPackages zu unterstützen, die für frühere Versionen geschrieben wurden. Wenn Sie jedoch über ein vorhandenes VSPackage verfügen, empfiehlt es sich, es auf die neue Technologie zu aktualisieren, um eine bessere Leistung und Zuverlässigkeit zu erzielen.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|BESCHREIBUNG|  
|-----------|-----------------|  
|[Erstellen einer Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Einführung in die Verwendung der Editor-Element Vorlagen.|  
|[Erweitern des Editors und der Sprachdienste](../extensibility/extending-the-editor-and-language-services.md)|Links zu Dokumenten, die den Entwurf und die Features des Kern Editors einführen und zeigen, wie Sie erweitert werden.|  
|[Legacyschnittstelle im Editor](../extensibility/legacy-interfaces-in-the-editor.md)|Links zu Dokumenten, in denen erläutert wird, wie Sie aus vorhandenem Code auf den Core-Editor zugreifen.|  
|[Erstellen von benutzerdefinierten Editoren und Designern](../extensibility/creating-custom-editors-and-designers.md)|Links zu Dokumenten, die erläutern, wie benutzerdefinierte Editoren erstellt werden.|  
|[Erweiterbarkeit von Legacysprachdiensten](../extensibility/internals/legacy-language-service-extensibility.md)|Links zu Dokumenten, in denen beschrieben wird, wie Programmiersprachen in Visual Studio integriert werden.|  
|[Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Führt die Managed Extensibility Framework (MEF) ein.|  
|[Windows Presentation Foundation](https://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Führt die Windows Presentation Foundation (WPF) ein.|
