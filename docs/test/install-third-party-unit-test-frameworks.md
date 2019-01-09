---
title: Installieren von Frameworks für Komponententests von Drittanbietern
ms.date: 06/07/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: f8cdfa96e41e72531cb3f2cdc164af4ed57546e5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955239"
---
# <a name="install-unit-test-frameworks"></a>Installieren von Komponententestframeworks

Im Visual Studio-Test-Explorer kann jedes beliebige Framework für Komponententests ausgeführt werden, für den eine Adapterschnittstelle für den Explorer entwickelt wurde. Das Installationsprogramm des Frameworks installiert die Binarys und fügt Visual Studio-Projektvorlagen für die von ihm unterstützten Sprachen hinzu. Wenn Sie ein Projekt mit der Vorlage erstellen, wird das Framework beim Test-Explorer registriert. Eine Visual Studio-Projektmappe kann Komponententestprojekte enthalten, die verschiedene Frameworks verwenden und verschiedene Zielsprachen aufweisen. Der Test-Explorer kann sie alle ausführen.

[MSTest](getting-started-with-unit-testing.md) ist das Testframework von Visual Studio und wird standardmäßig mit Visual Studio installiert.

## <a name="acquire-frameworks"></a>Herunterladen von Frameworks

Sie können Komponententest-Frameworks von Drittanbietern oder [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) herunterladen und mithilfe des Visual Studio-Erweiterungs-Managers installieren. Frameworks können außerdem von anderen Websites, wie etwa der Website des Frameworks, heruntergeladen werden.

### <a name="install-from-visual-studio"></a>Installieren aus Visual Studio

1. Wählen Sie im Standardmenü **Tools** und dort **Erweiterungen und Updates** aus.

2. Erweitern Sie **Online** > **Visual Studio Marketplace** > **Extras**. Wählen Sie **Test** aus.

3. Suchen Sie das Framework in der Liste.

4. Wählen Sie das Framework und dann **Herunterladen** aus.

Weitere Informationen finden Sie unter [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md).

### <a name="install-from-the-web"></a>Installation aus dem Web

Wenn Sie das Framework kennen, für das Sie sich interessieren:

1. Öffnen Sie [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

2. Geben Sie den Namen des Frameworks im Feld **Suchen** ein.

3. Wählen Sie in der Ergebnisliste das Framework aus, um im **Visual Studio Marketplace** zur Seite für das Tool zu gelangen.

So durchsuchen Sie eine Liste der Frameworks und anderer Testtools:

1. Öffnen Sie [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

2. Klicken Sie unter **Nach Kategorie/Sammlung filtern**, auf **Alle anzeigen**.

3. Erweitern Sie in der Liste **Kategorie** (als **Anzeigen** gekennzeichnet) den Knoten **Extras**, und klicken Sie auf **Testen**.

4. Wählen Sie in der Ergebnisliste ein Framework aus, um zu einer **Visual Studio Marketplace**-Seite für das Tool zu gelangen.

## <a name="update-to-the-latest-test-adapters"></a>Aktualisieren auf die neuesten Testadapter

Aktualisieren Sie auf den neuesten stabilen Testadapter, um eine bessere Testermittlung und Ausführung zu erzielen. Weitere Informationen über Updates für MSTest-, NUnit- und xUnit-Testadapter finden Sie im [Visual Studio-Blog](https://blogs.msdn.microsoft.com/visualstudio/2017/11/16/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>So aktualisieren Sie auf die neueste stabile Testadapterversion

1. Öffnen Sie den NuGet-Paket-Manager für Ihre Projektmappe, indem Sie zu **Extras** > **NuGet-Paket-Manager** > **NuGet-Pakete für Projektmappe verwalten** navigieren.

2. Klicken Sie auf die Registerkarte **Updates**, und suchen Sie nach installierten MSTest-, NUnit- oder xUnit-Testadaptern.

3. Wählen Sie erst alle Testadapter und dann im Dropdownmenü die neueste stabile Version aus.

4. Wählen Sie die Schaltfläche **Installieren** aus.

   ![Aktualisieren des Testadapters](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Siehe auch

- [Ausführen von Komponententests für Code](../test/unit-test-your-code.md)
