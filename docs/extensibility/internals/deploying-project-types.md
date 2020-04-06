---
title: Bereitstellen von Projekttypen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 835e85ade4d309d0b5692aa9b857476cd6b5927a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708787"
---
# <a name="deploy-project-types"></a>Bereitstellen von Projekttypen
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]installiert einen neuen Projektaggregator (*ProjectAggregator2.dll*) sowie ein Windows Installer-Paket zur Umverteilung (*ProjectAggregator2.msi*). Sie müssen den neuen Aggregator für Projekttypen mit verwaltetem Code verwenden. ProjectAggregator2 umgeht Einschränkungen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] im Projektaggregator, die verhindern, dass Projekttypen mit verwaltetem Code ordnungsgemäß funktionieren. In den folgenden Schritten wird beschrieben, wie Sie Ihr VSPackage so ändern, dass es den neuen Aggregator verwendet.

1. Entfernen Sie das NativeHierarchyWrapper-Projekt aus Ihrer Projektmappe.

2. Entfernen Sie alle NativeHierarchyWrapper-Binärdateien aus Ihrem Setup.

3. Fügen Sie *ProjectAggregator2.msi* zu Ihrem Setup hinzu.
