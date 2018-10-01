---
title: Bereitstellen von Projekttypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 66069ac71fbe59e8b63126d66d2a0cc63ed095bc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513514"
---
# <a name="deploying-project-types"></a>Bereitstellen von Projekttypen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Projekttypen bereitstellen](https://docs.microsoft.com/visualstudio/extensibility/internals/deploying-project-types).  
  
[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] installiert einen neuen Projekttyp Aggregator (ProjectAggregator2.dll) und auch ein Windows Installer-Paket für die weiterverteilung (ProjectAggregator2.msi). Sie müssen den neuen Aggregator für Projekttypen von verwaltetem Code verwenden. ProjectAggregator2 funktioniert problemumgehungen Einschränkungen in der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Projekt Aggregator, die verhindern, dass Projekttypen von verwaltetem Code ordnungsgemäß funktioniert. Die folgenden Schritte beschreiben, wie Sie Ihr VSPackage für die Verwendung des neuen Aggregators zu ändern.  
  
1.  Entfernen Sie das Projekt NativeHierarchyWrapper aus der Projektmappe.  
  
2.  Entfernen Sie alle NativeHierarchyWrapper-Binärdateien aus dem Setup.  
  
3.  Fügen Sie auf Ihr Setup ProjectAggregator2.msi hinzu.

