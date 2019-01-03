---
title: Editoren und Sprachen Service Extensions | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b4182af1731dec583a555031b90be1315e6a5d9c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927479"
---
# <a name="editor-and-language-service-extensions"></a>Service-Erweiterungen, Editoren und Sprachen
Sie können die meisten Visual Studio Code-Editor-Funktionen erweitern. Der Editor basiert auf der Windows Presentation Foundation (WPF) und in verwaltetem Code geschrieben wird. Obwohl es sich bei diesem Entwurf die Entwürfe in früheren Versionen von Visual Studio unterscheidet, bietet sie größtenteils die gleichen Funktionen. Um den Editor zu erweitern, verwenden Sie das Managed Extensibility Framework (MEF).  
  
 Visual Studio SDK stellt Adapter, die als bekannt *Shims* VSPackages zu unterstützen, die für frühere Versionen geschrieben wurden. Wenn Sie einen vorhandenen VSPackage verfügen, empfehlen wir dennoch, dass Sie es, um die neue Technologie aktualisieren, um eine bessere Leistung und Zuverlässigkeit zu erhalten.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Erstellen Sie eine Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Einführung in die Editor-Elementvorlagen mit.|  
|[Erweitern Sie die Dienste, Editoren und Sprachen](../extensibility/extending-the-editor-and-language-services.md)|Enthält Links zu Dokumenten, die eingeführt werden, den Entwurf und die Funktionen von der Kern-Editor, und zeigen, wie Sie sie erweitern.|  
|[Legacy-Schnittstellen im editor](../extensibility/legacy-interfaces-in-the-editor.md)|Enthält Links zu Dokumenten, die erläutern, wie Sie auf die Kern-Editor aus vorhandenem Code zugreifen.|  
|[Erstellen von benutzerdefinierten Editoren und Designern](../extensibility/creating-custom-editors-and-designers.md)|Enthält Links zu Dokumenten, die erläutern, wie Sie benutzerdefinierte Editoren zu erstellen.|  
|[Erweiterbarkeit von legacysprachdiensten](../extensibility/internals/legacy-language-service-extensibility.md)|Enthält Links zu Dokumenten, die beschreiben, wie Sie Programmiersprachen in Visual Studio zu integrieren.|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Wird das Managed Extensibility Framework (MEF) eingeführt.|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Führt die Windows Presentation Foundation (WPF).|