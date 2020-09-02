---
title: Codeanalyse für verwalteten Code
ms.date: 08/27/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d13a8afdfcbeb6ae9f91e39779af8b82b2461000
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "89091399"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Übersicht über die Code Analyse für .net in Visual Studio

Visual Studio kann eine Code Analyse von verwaltetem Code auf zweierlei Weise durchführen: mit [Legacy Analyse](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), auch als "FxCop Static Analysis of Managed Assemblys" bezeichnet, und mit den moderneren [.NET Compiler Platform basierten Code](../code-quality/roslyn-analyzers-overview.md)Analysemodulen. .NET Compiler Platform basierten Code Analysen, die Ihren Code während der durch zugabeart analysieren, ersetzen Sie die statische Code Analyse der veralteten FxCop-Code, die nur kompilierten Code analysiert.
