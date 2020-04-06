---
title: Editor- und Sprachdiensterweiterungen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e37165dc5fe9ac010545304218e807d923b424b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712020"
---
# <a name="editor-and-language-service-extensions"></a>Editor- und Sprachdiensterweiterungen
Sie können die meisten Funktionen des Visual Studio-Code-Editors erweitern. Der Editor basiert auf der Windows Presentation Foundation (WPF) und wird in verwaltetem Code geschrieben. Obwohl sich dieser Entwurf von den Entwürfen in früheren Versionen von Visual Studio unterscheidet, bietet er die meisten der gleichen Features. Um den Editor zu erweitern, verwenden Sie das Managed Extensibility Framework (MEF).

 Das Visual Studio SDK stellt Adapter bereit, die als *Shims* bezeichnet werden, um VSPackages zu unterstützen, die für frühere Versionen geschrieben wurden. Wenn Sie jedoch über ein vorhandenes VSPackage verfügen, empfehlen wir Ihnen, es auf die neue Technologie zu aktualisieren, um eine bessere Leistung und Zuverlässigkeit zu erzielen.

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Erstellen einer Erweiterung mit einer Editorelementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Einführung in die Verwendung der Editor-Elementvorlagen.|
|[Erweitern der Editor- und Sprachdienste](../extensibility/extending-the-editor-and-language-services.md)|Links zu Dokumenten, die das Design und die Funktionen des Kerneditors vorstellen und zeigen, wie sie erweitert werden.|
|[Legacy-Schnittstellen im Editor](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)|Links zu Dokumenten, die den Zugriff auf den Kerneditor aus vorhandenem Code erklären.|
|[Erstellen benutzerdefinierter Editoren und Designer](../extensibility/creating-custom-editors-and-designers.md)|Links zu Dokumenten, die das Erstellen benutzerdefinierter Editoren erläutern.|
|[Erweiterbarkeit des Legacy-Sprachdienstes](../extensibility/internals/legacy-language-service-extensibility.md)|Links zu Dokumenten, die beschreiben, wie Programmiersprachen in Visual Studio integriert werden.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Führt das Managed Extensibility Framework (MEF) ein.|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Stellt die Windows Presentation Foundation (WPF) vor.|
