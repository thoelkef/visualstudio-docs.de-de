---
title: Editor und Language Service Erweiterungen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d2fceb0487c23dc34d3f4f4937d7a5998340ae3d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="editor-and-language-service-extensions"></a>Editor und Spracherweiterungen-Dienst
Sie können die meisten Funktionen von Visual Studio Code-Editor erweitern. Der Editor basiert auf Windows Presentation Foundation (WPF) und in verwaltetem Code geschrieben wird. Obwohl dieses Design aus der entwirft in früheren Versionen von Visual Studio im Detail variiert, stellt er größtenteils die gleichen Funktionen bereit. Um den Editor zu erweitern, verwenden Sie die Managed Extensibility Framework (MEF).  
  
 Das Visual Studio SDK stellt Adapter, die als bekannte *Shims* VSPackages zu unterstützen, die für frühere Versionen geschrieben wurden. Wenn Sie ein VSPackage vorhandene verfügen, empfehlen wir trotzdem, dass Sie sie, um die neue Technologie aktualisieren, die eine bessere Leistung und Zuverlässigkeit zu erhalten.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Erstellen einer Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Einführung in die Verwendung von Elementvorlagen Editor.|  
|[Erweitern des Editors und der Sprachdienste](../extensibility/extending-the-editor-and-language-services.md)|Links zu Dokumenten, die das Design und die Funktionen des Editors Core eingeführt und zeigen, wie Sie es erweitern.|  
|[Legacy-Schnittstellen im Editor](../extensibility/legacy-interfaces-in-the-editor.md)|Links zu Dokumenten, die erläutern, wie die Core-Editor aus vorhandenem Code zugreifen.|  
|[Erstellen von benutzerdefinierten Editoren und Designern](../extensibility/creating-custom-editors-and-designers.md)|Links zu Dokumenten, die erläutern, wie benutzerdefinierte Editoren erstellt.|  
|[Erweiterbarkeit von Legacysprachdiensten](../extensibility/internals/legacy-language-service-extensibility.md)|Links zu Dokumenten, die beschreiben, wie Sie Programmiersprachen in Visual Studio integrieren.|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Führt das Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Führt ein Windows Presentation Foundation (WPF).|