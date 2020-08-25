---
title: Codeanalyse für verwalteten Code
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e6515c0df7a9c3389e754d5238788d716be49e2e
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800085"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Übersicht über die Code Analyse für verwalteten Code in Visual Studio

Visual Studio kann eine Code Analyse von verwaltetem Code auf zwei Arten durchführen:
- Mit der [Legacy Analyse](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), auch als "FxCop Static Analysis of Managed Assemblys" bezeichnet.
- Mit den moderneren [.NET Compiler Platform basierten Code Analysen](../code-quality/roslyn-analyzers-overview.md). .NET Compiler Platform basierten Code Analysen, die Ihren Code während der durch zugabeart analysieren, ersetzen Sie die statische Code Analyse der veralteten FxCop-Code, die nur kompilierten Code analysiert.