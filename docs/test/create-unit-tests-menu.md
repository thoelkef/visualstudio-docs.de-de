---
title: "Erstellen von Stubs für Unittestmethoden mit dem Befehl „Unittests erstellen“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: unit testing, create unit tests
ms.assetid: 5D625021-BA96-48A5-9453-3EF6F0943466
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: c1bd2d883a86a74ee79ced5bf857e3c81c019c5c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>Erstellen von Stubs für Unittestmethoden mit dem Befehl „Unittests erstellen“

Mit dem Befehl **Unittests erstellen** von Visual Studio können Sie Stubs für Unittestmethoden erstellen. Diese Funktion ermöglicht die leichte Konfiguration von Testprojekten, Testklassen und des darin enthaltenen Testmethodenstubs. 

## <a name="availability-and-extensions"></a>Verfügbarkeit und Erweiterungen

Der Menübefehl **Unittests erstellen**:

* ist in den Editionen Community, Professional und Enterprise von Visual Studio 2015 und höher verfügbar

* unterstützt nur C#-Code, der das .NET Framework als Ziel hat

* ist [erweiterbar](#extend-framework) und unterstützt das Ausgeben von Tests im Format MSTest, MSTest V2, NUnit und xUnit

## <a name="get-started"></a>Erste Schritte

Beginnen Sie, indem Sie eine Methode, einen Typ oder einen Namespace im Code.Editor im zu testenden Projekt auswählen. Öffnen Sie dann das Kontextmenü, und klicken Sie auf **Unittests erstellen**. Dadurch wird das Dialogfeld **Unittest erstellen**, wo Sie die Erstelloptionen für den neuen Unittest auswählen können.

![Verwenden des Befehls „Unittests erstellen“](media/createunittestcommand.png)

## <a name="setting-unit-test-traits"></a>Festlegen der Merkmale eines Unittests

Wenn Sie diese Tests im Rahmen des Testautomatisierungsprozesses ausführen möchten, ziehen Sie in Erwägung, den Test in einem anderen Testprojekt zu erstellen (die zweite Option ist das oben stehende Dialogfeld) und Unittestmerkmale für den Unittest festzulegen. So können Sie diese Tests leichter als Teil der Continuous Integration- und Continuous Deployment-Pipeline ein- oder ausschließen. Sie können die Merkmale festlegen, indem Sie Metadaten direkt in den Unittest einfügen, wie unten dargestellt. 

![Festlegen der Merkmale eines Unittests](media/createunittest.png)

<a name="extend-framework"></a>
## <a name="using-third-party-unit-test-frameworks"></a>Verwenden von Unittestframeworks von Drittanbietern

Mit Visual Studio können Sie Unittest mit jedem Testframework leicht erstellen. Um andere Testframeworks hinzuzufügen, klicken Sie auf **Extras > Erweiterungen und Updates**.
Erweitern Sie **Online**, **Visual Studio Gallery**, **Tools**, und klicken Sie dann auf **Test**. 

![Verwenden von Testframeworks von Drittanbietern](media/createunittestfx.png)

Testframeworkerweiterungen sind im Visual Studio Marketplace verfügbar:

* [NUnit-Erweiterung für die Testgeneratoren](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [xUnit.net-Erweiterung für die Testgeneratoren](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>Wann ist diese Funktion sinnvoll?

Verwenden Sie diese Funktion, wenn Sie Unittest erstellen müssen, insbesondere wenn Sie vorhandenen Code testen, der sehr wenig oder keine Testabdeckung oder keine Dokumentation aufweist. Also dort, wo es sehr eingeschränkte oder gar keine Codespezifikationen gibt. Effektiv implementiert sie eine Vorgehensweise, die den [Intelligenten Unittests](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/19/introducing-smart-unit-tests.aspx) ähnelt, die das beobachtete Verhalten des Codes charakterisieren.

Diese Funktion kann jedoch auch auf Situationen angewendet werden, in denen der Entwickler beginnt, indem er Code schreibt und diesen dann dazu verwendet, die Unittests zu bootstrappen. Es kann sein, dass der Entwickler beim Codieren schnell einen Stub für Unittestmethoden für einen bestimmten Codeteil erstellen möchte (mit einer entsprechenden Testklasse und einem entsprechenden Testprojekt). 

## <a name="more-information"></a>Weitere Informationen

Im Blogpost [Creating unit test method stubs with "Create Unit Tests" (Erstellen von Stubs für Unittestmethoden mit "Unittests erstellen")](https://blogs.msdn.microsoft.com/visualstudioalm/2015/03/06/creating-unit-test-method-stubs-with-create-unit-tests/).

Weitere Blogposts zu Unittests finden Sie [hier](https://blogs.msdn.microsoft.com/visualstudioalm/tag/unit-testing/).
