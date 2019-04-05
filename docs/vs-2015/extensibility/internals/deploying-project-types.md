---
title: Bereitstellen von Projekttypen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f168656950c65ce133a8e808a0fa1232726e1b5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955781"
---
# <a name="deploying-project-types"></a>Bereitstellen von Projekttypen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] installiert einen neuen Projekttyp Aggregator (ProjectAggregator2.dll) und auch ein Windows Installer-Paket für die weiterverteilung (ProjectAggregator2.msi). Sie müssen den neuen Aggregator für Projekttypen von verwaltetem Code verwenden. ProjectAggregator2 funktioniert problemumgehungen Einschränkungen in der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Projekt Aggregator, die verhindern, dass Projekttypen von verwaltetem Code ordnungsgemäß funktioniert. Die folgenden Schritte beschreiben, wie Sie Ihr VSPackage für die Verwendung des neuen Aggregators zu ändern.  
  
1.  Entfernen Sie das Projekt NativeHierarchyWrapper aus der Projektmappe.  
  
2.  Entfernen Sie alle NativeHierarchyWrapper-Binärdateien aus dem Setup.  
  
3.  Fügen Sie auf Ihr Setup ProjectAggregator2.msi hinzu.
