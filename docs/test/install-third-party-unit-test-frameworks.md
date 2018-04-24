---
title: Installieren von Frameworks für Komponententests von Drittanbietern in Visual Studio | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 93502e0d3a3425c4debcff4f181263dc4e58d9b7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="install-third-party-unit-test-frameworks"></a>Installieren von Frameworks für Komponententests von Drittanbietern

Im Visual Studio-Test-Explorer kann jedes beliebige Framework für Komponententests ausgeführt werden, für den eine Adapterschnittstelle für den Explorer entwickelt wurde. Das Installationsprogramm des Frameworks installiert die Binarys und fügt Visual Studio-Projektvorlagen für die von ihm unterstützten Sprachen hinzu. Wenn Sie ein Projekt mit der Vorlage erstellen, wird das Framework beim Test-Explorer registriert. Eine Visual Studio-Projektmappe kann Komponententestprojekte enthalten, die verschiedene Frameworks verwenden und verschiedene Zielsprachen aufweisen. Der Test-Explorer kann sie alle ausführen.

## <a name="acquiring-third-party-frameworks"></a>Erwerb von Drittanbieter-Frameworks

Sie können viele Komponententest-Frameworks von Drittanbietern oder Visual Studio Marketplace herunterladen und mithilfe des Visual Studio-Erweiterungs-Managers installieren. Frameworks können außerdem von anderen Websites, wie etwa der Website des Frameworks, heruntergeladen werden.

### <a name="installing-from-visual-studio"></a>Installieren in Visual Studio

1. Wählen Sie im Standardmenü **Tools** und dort **Erweiterungen und Updates** aus.

2. Erweitern Sie **Online** > **Visual Studio Marketplace** > **Extras**. Wählen Sie **Test** aus.

3. Suchen Sie das Framework in der Liste.

4. Wählen Sie das Framework und dann **Herunterladen** aus.

Weitere Informationen finden Sie unter [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md).

### <a name="installing-from-the-web"></a>Installation aus dem Web

Wenn Sie das Framework kennen, für das Sie sich interessieren:

1. Öffnen Sie [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

2. Geben Sie den Namen des Frameworks im Feld **Suchen** ein.

3. Wählen Sie in der Ergebnisliste das Framework aus, um im Visual Studio Marketplace zur Seite für das Tool zu gelangen.

So durchsuchen Sie eine Liste der Frameworks und anderer Testtools:

1. Öffnen Sie [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

2. Klicken Sie unter **Nach Kategorie/Sammlung filtern**, auf **Alle anzeigen**.

3. Erweitern Sie in der Liste **Kategorie** (als **Anzeigen** gekennzeichnet) den Knoten **Extras**, und klicken Sie auf **Testen**.

4. Wählen Sie in der Ergebnisliste ein Framework aus, um zu einer Visual Studio Marketplace-Seite für das Tool zu gelangen.

## <a name="see-also"></a>Siehe auch

- [Komponententest für Code](../test/unit-test-your-code.md)
