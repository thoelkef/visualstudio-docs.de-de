---
title: Erstellen von Stubs für Komponententestmethoden
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a71835274058dfb3a4e69fe052f07bcd073a2c7b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959004"
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>Erstellen von Stubs für Unittestmethoden mit dem Befehl „Unittests erstellen“

Mit dem Befehl **Unittests erstellen** von Visual Studio können Sie Stubs für Unittestmethoden erstellen. Diese Funktion ermöglicht die leichte Konfiguration von Testprojekten, Testklassen und des darin enthaltenen Testmethodenstubs.

## <a name="availability-and-extensions"></a>Verfügbarkeit und Erweiterungen

Der Menübefehl **Unittests erstellen**:

* ist in den Editionen Community, Professional und Enterprise von Visual Studio 2015 und höher verfügbar

* unterstützt nur C#-Code, der das .NET Framework als Ziel hat

* ist erweiterbar und unterstützt das Ausgeben von Tests im Format MSTest, MSTest V2, NUnit und xUnit.

* ist noch nicht für .NET Core-Projekte verfügbar.

## <a name="get-started"></a>Erste Schritte

Beginnen Sie, indem Sie eine Methode, einen Typ oder einen Namespace im Code.Editor im zu testenden Projekt auswählen. Öffnen Sie dann das Kontextmenü, und klicken Sie auf **Unittests erstellen**. Das Dialogfeld **Komponententests erstellen** wird geöffnet, in dem Sie die Erstelloptionen für den neuen Komponententests auswählen können.

![Verwenden des Befehls „Unittests erstellen“](media/createunittestcommand.png)

## <a name="setting-unit-test-traits"></a>Festlegen der Merkmale eines Unittests

Wenn Sie diese Tests im Rahmen des Testautomatisierungsprozesses ausführen möchten, ziehen Sie in Erwägung, den Test in einem anderen Testprojekt zu erstellen (die zweite Option ist das oben stehende Dialogfeld) und Merkmale für den Komponententest festzulegen. So können Sie diese Tests leichter als Teil der Continuous Integration- und Continuous Deployment-Pipeline ein- oder ausschließen. Sie können die Merkmale festlegen, indem Sie Metadaten direkt in den Unittest einfügen, wie unten dargestellt.

![Festlegen der Merkmale eines Unittests](media/createunittest.png)

## <a name="using-third-party-unit-test-frameworks"></a>Verwenden von Unittestframeworks von Drittanbietern

Mit Visual Studio können Sie Unittest mit jedem Testframework leicht erstellen. Zur Installation anderer Frameworks:

1. Wählen Sie **Tools** > **Erweiterungen und Updates** aus.
2. Erweitern Sie **Online** > **Visual Studio Marketplace** > **Extras**, und wählen Sie dann **Testing** aus.

![Verwenden von Testframeworks von Drittanbietern](media/createunittestfx.png)

Testframeworkerweiterungen sind im Visual Studio Marketplace verfügbar:

* [NUnit-Erweiterung für die Testgeneratoren](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [xUnit.net-Erweiterung für die Testgeneratoren](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>Wann ist diese Funktion sinnvoll?

Verwenden Sie dieses Feature, wenn Sie Komponententests erstellen müssen, insbesondere wenn Sie vorhandenen Code testen, der wenig oder keine Testabdeckung und keine Dokumentation aufweist. Also dort, wo es sehr eingeschränkte oder gar keine Codespezifikationen gibt. Im Prinzip implementiert sie einen Ansatz, der den [intelligenten Komponententests](https://blogs.msdn.microsoft.com/devops/2014/11/19/introducing-smart-unit-tests/) ähnelt, die das beobachtete Verhalten des Codes charakterisieren.

Diese Funktion kann jedoch auch auf Situationen angewendet werden, in denen der Entwickler beginnt, indem er Code schreibt und diesen dann dazu verwendet, die Unittests zu bootstrappen. Es kann sein, dass der Entwickler beim Codieren schnell einen Stub für Unittestmethoden für einen bestimmten Codeteil erstellen möchte (mit einer entsprechenden Testklasse und einem entsprechenden Testprojekt).

## <a name="see-also"></a>Siehe auch

- [Creating unit test method stubs with "Create Unit Tests" (Erstellen von Stubs für Unittestmethoden mit "Unittests erstellen")](https://blogs.msdn.microsoft.com/devops/2015/03/06/creating-unit-test-method-stubs-with-create-unit-tests/)
- [Blogbeiträge zu Komponententests](https://blogs.msdn.microsoft.com/devops/?s=unit+testing)
