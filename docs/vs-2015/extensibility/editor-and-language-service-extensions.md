---
title: Editoren und Sprachen Service Extensions | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b5e0b568cee873d29f73eb2b81e38d49b76b5844
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778760"
---
# <a name="editor-and-language-service-extensions"></a>Editor- und Sprachdiensterweiterungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die meisten Visual Studio Code-Editor-Funktionen erweitern. Der Editor basiert auf der Windows Presentation Foundation (WPF) und in verwaltetem Code geschrieben wird. Obwohl es sich bei diesem Entwurf die Entwürfe in früheren Versionen von Visual Studio unterscheidet, bietet sie größtenteils die gleichen Funktionen. Um den Editor zu erweitern, verwenden Sie das Managed Extensibility Framework (MEF).  
  
 Visual Studio SDK stellt Adapter, die als bekannt *Shims* VSPackages zu unterstützen, die für frühere Versionen geschrieben wurden. Wenn Sie einen vorhandenen VSPackage verfügen, empfehlen wir dennoch, dass Sie es, um die neue Technologie aktualisieren, um eine bessere Leistung und Zuverlässigkeit zu erhalten.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Erstellen einer Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Einführung in die Editor-Elementvorlagen mit.|  
|[Erweitern des Editors und der Sprachdienste](../extensibility/extending-the-editor-and-language-services.md)|Enthält Links zu Dokumenten, die eingeführt werden, den Entwurf und die Funktionen von der Kern-Editor, und zeigen, wie Sie sie erweitern.|  
|[Legacyschnittstelle im Editor](../extensibility/legacy-interfaces-in-the-editor.md)|Enthält Links zu Dokumenten, die erläutern, wie Sie auf die Kern-Editor aus vorhandenem Code zugreifen.|  
|[Erstellen von benutzerdefinierten Editoren und Designern](../extensibility/creating-custom-editors-and-designers.md)|Enthält Links zu Dokumenten, die erläutern, wie Sie benutzerdefinierte Editoren zu erstellen.|  
|[Erweiterbarkeit von Legacysprachdiensten](../extensibility/internals/legacy-language-service-extensibility.md)|Enthält Links zu Dokumenten, die beschreiben, wie Sie Programmiersprachen in Visual Studio zu integrieren.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Wird das Managed Extensibility Framework (MEF) eingeführt.|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Führt die Windows Presentation Foundation (WPF).|

