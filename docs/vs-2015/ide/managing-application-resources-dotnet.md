---
title: Verwalten von Anwendungsressourcen (.NET) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: efe2b176db9f6f22f9e38775d5fc8acad87655ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651388"
---
# <a name="managing-application-resources-net"></a>Verwalten von Anwendungsressourcen (.NET)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ressourcendateien sind Dateien, die Teil einer Anwendung sind, jedoch noch nicht kompiliert sind, beispielsweise Symboldateien oder Audiodateien. Da diese Dateien nicht Teil des Kompilierungsprozesses sind, können Sie sie ändern, ohne Ihre Binärdateien neu zu kompilieren. Wenn Sie beabsichtigen, die Anwendung zu lokalisieren, verwenden Sie beim Lokalisieren Ressourcendateien für alle Zeichenfolgen und anderen Ressourcen, die geändert werden müssen.

 Weitere Informationen zu Ressourcen in .NET-Desktop-Apps finden Sie unter [Resources in Desktop Apps](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890). Weitere Informationen zu Ressourcen in C++-Desktop-Apps finden Sie unter [Working with Resource Files](https://msdn.microsoft.com/library/2699a539-b369-4b78-80f0-df03eb7b6780).

 Windows Store-Apps verwendet ein anderes Ressourcenmodell von Desktop-Apps. Weitere Informationen zu Ressourcen in Windows Store-Apps finden Sie auf der Windows Developer Center-Website unter [Definieren von App-Ressourcen](https://msdn.microsoft.com/library/windows/apps/hh465228.aspx) .

## <a name="working-with-resources"></a>Arbeiten mit Ressourcen
 Öffnen Sie in einem Projekt mit verwaltetem Code das Projekteigenschaftenfenster (klicken Sie mit der rechten Maustaste auf den Projektknoten im **Projektmappen-Explorer** , und wählen Sie **Eigenschaften**aus, geben Sie **Projekteigenschaften** im Fenster **Schnellstart** ein, oder drücken Sie innerhalb des Fensters **Projektmappen-Explorer** ALT+EINGABE). Wählen Sie die Registerkarte **Ressourcen** aus. Sie können eine RESX-Datei hinzufügen, wenn das Projekt noch keine enthält, verschiedene Arten von Ressourcen hinzufügen und löschen und vorhandene Ressourcen ändern.

 Informationen zur Bearbeitung von Ressourcen in C++-Projekten finden Sie unter [How to: Create a Resource](https://msdn.microsoft.com/library/aad44914-9145-45a3-a7d8-9de89b366716).
