---
title: Verwalten von Anwendungsressourcen (.NET)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe35a9a0e9b1e4b2e04e978f2b32cb38439b76cd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="manage-application-resources-net"></a>Verwalten von Anwendungsressourcen (.NET)

Ressourcendateien sind Dateien, die Teil einer Anwendung sind, jedoch noch nicht kompiliert sind, beispielsweise Symboldateien oder Audiodateien. Da diese Dateien nicht Teil des Kompilierungsprozesses sind, können Sie sie ändern, ohne Ihre Binärdateien neu zu kompilieren. Wenn Sie beabsichtigen, die Anwendung zu lokalisieren, verwenden Sie beim Lokalisieren Ressourcendateien für alle Zeichenfolgen und anderen Ressourcen, die geändert werden müssen.

Weitere Informationen zu Ressourcen in .NET-Desktop-Apps finden Sie unter [Resources in desktop apps (Ressourcen in Desktop-Apps)](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Arbeiten mit Ressourcen

Öffnen Sie das Projekteigenschaftenfenster in einem Projekt mit verwaltetem Code. Sie können das Eigenschaftenfenster öffnen, indem Sie Folgendes durchführen:

- Klicken Sie mit der rechten Maustaste auf den Projektknoten im **Projektmappen-Explorer** und dann auf **Eigenschaften**.
- Geben Sie „Projekteigenschaften“ in das **Schnellstart**-Fenster ein.
- Drücken Sie im **Projektmappen-Explorer** die Tasten **ALT**+**EINGABETASTE**.

Wählen Sie die Registerkarte **Ressourcen** aus. Sie können eine *RESX-Datei* hinzufügen, wenn das Projekt noch keine enthält, sowie verschiedene Arten von Ressourcen hinzufügen und löschen und vorhandene Ressourcen ändern.

## <a name="resources-in-other-project-types"></a>Ressourcen in anderen Projekttypen

Ressourcen werden in .NET-Projekten anders verwaltet als in anderen Projekttypen. Weitere Informationen zu folgenden Themen finden Sie unter:

- zu Universelle Windows-Plattform-Apps (UWP): [App-Ressourcen und das Ressourcenverwaltungssystem](/windows/uwp/app-resources/)
- Weitere Informationen zu C++-Projekten finden Sie unter [Arbeiten mit Ressourcendateien](/cpp/windows/working-with-resource-files) und [Vorgehensweise: Erstellen einer Ressource](/cpp/windows/how-to-create-a-resource).

## <a name="see-also"></a>Siehe auch

- [Ressourcen in Desktop-Apps (.NET Framework)](/dotnet/framework/resources/index)
