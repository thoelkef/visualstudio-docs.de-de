---
title: Bereitstellen von Projekttypen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 958628194e4ea768de5a47dc66476345bff6c4f3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56625334"
---
# <a name="deploy-project-types"></a>Bereitstellen von Projekttypen
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] installiert einen neuen Projekttyp Aggregator (*ProjectAggregator2.dll*) und auch ein Windows Installer-Paket für die weiterverteilung (*ProjectAggregator2.msi*). Sie müssen den neuen Aggregator für Projekttypen von verwaltetem Code verwenden. ProjectAggregator2 umgeht Einschränkungen in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt Aggregator, der verhindert, dass Projekttypen von verwaltetem Code ordnungsgemäß funktioniert. Die folgenden Schritte beschreiben, wie Sie Ihr VSPackage für die Verwendung des neuen Aggregators zu ändern.

1.  Entfernen Sie das Projekt NativeHierarchyWrapper aus der Projektmappe.

2.  Entfernen Sie alle NativeHierarchyWrapper-Binärdateien aus dem Setup.

3.  Hinzufügen *ProjectAggregator2.msi* auf Ihr Setup.