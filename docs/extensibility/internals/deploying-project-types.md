---
title: Bereitstellen von Projekttypen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac03682fa1158f5da9c694cf1be5282717c07b55
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312179"
---
# <a name="deploy-project-types"></a>Bereitstellen von Projekttypen
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] installiert einen neuen Projekttyp Aggregator (*ProjectAggregator2.dll*) und auch ein Windows Installer-Paket für die weiterverteilung (*ProjectAggregator2.msi*). Sie müssen den neuen Aggregator für Projekttypen von verwaltetem Code verwenden. ProjectAggregator2 umgeht Einschränkungen in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt Aggregator, der verhindert, dass Projekttypen von verwaltetem Code ordnungsgemäß funktioniert. Die folgenden Schritte beschreiben, wie Sie Ihr VSPackage für die Verwendung des neuen Aggregators zu ändern.

1. Entfernen Sie das Projekt NativeHierarchyWrapper aus der Projektmappe.

2. Entfernen Sie alle NativeHierarchyWrapper-Binärdateien aus dem Setup.

3. Hinzufügen *ProjectAggregator2.msi* auf Ihr Setup.