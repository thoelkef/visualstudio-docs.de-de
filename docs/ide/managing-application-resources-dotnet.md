---
title: Verwalten von Anwendungsressourcen (.NET) | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b599a919911fcc5d2833cfe69b75f7b32cced858
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="managing-application-resources-net"></a>Verwalten von Anwendungsressourcen (.NET)
Ressourcendateien sind Dateien, die Teil einer Anwendung sind, jedoch noch nicht kompiliert sind, beispielsweise Symboldateien oder Audiodateien. Da diese Dateien nicht Teil des Kompilierungsprozesses sind, können Sie sie ändern, ohne Ihre Binärdateien neu zu kompilieren. Wenn Sie beabsichtigen, die Anwendung zu lokalisieren, verwenden Sie beim Lokalisieren Ressourcendateien für alle Zeichenfolgen und anderen Ressourcen, die geändert werden müssen.  
  
Weitere Informationen zu Ressourcen in .NET-Desktop-Apps finden Sie unter [Resources in Desktop Apps](/dotnet/framework/resources/index). Weitere Informationen zu Ressourcen in C++-Desktop-Apps finden Sie unter [Working with Resource Files](/cpp/windows/working-with-resource-files).  
  
UWP-Anwendungen verwenden ein anderes Ressourcenmodell als Desktop-Apps. Informationen über Ressourcen in Windows 8.x-Anwendungen finden Sie unter [Definieren von App-Ressourcen (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx).  
  
## <a name="working-with-resources"></a>Arbeiten mit Ressourcen  
Öffnen Sie das Projekteigenschaftenfenster in einem Projekt mit verwaltetem Code. Sie können das Eigenschaftenfenster öffnen, indem Sie Folgendes durchführen:

- Klicken Sie mit der rechten Maustaste auf den Projektknoten im **Projektmappen-Explorer** und dann auf **Eigenschaften**.
- Geben Sie **Projekteigenschaften** im **Schnellstart**-Fenster ein.
- Drücken Sie **ALT+EINGABETASTE** im **Projektmappen-Explorer**-Fenster.

Wählen Sie die Registerkarte **Ressourcen** aus. Sie können eine RESX-Datei hinzufügen, wenn das Projekt noch keine enthält, verschiedene Arten von Ressourcen hinzufügen und löschen und vorhandene Ressourcen ändern.  
  
Informationen zur Bearbeitung von Ressourcen in C++-Projekten finden Sie unter [How to: Create a Resource](/cpp/windows/how-to-create-a-resource).