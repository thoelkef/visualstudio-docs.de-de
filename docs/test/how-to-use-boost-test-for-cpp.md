---
title: "Verwenden von Boost.Test für C++ in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0710a8-8e8a-4f6e-8415-5ab3eb830079
caps.latest.revision: "14"
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6bfce4aa4153d8f01fa9ef6cd6dc0d4b08eedbc4
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2017
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Verwenden von Boost.Test für C++ in Visual Studio
In **Visual Studio 2017-Version 15.5** und höher ist Boost.Test als Standardkomponente der Workload **Desktopentwicklung mit C++** in die Visual Studio-IDE integriert. Um die Workload auf Ihrem Computer zu installieren, öffnen Sie den Visual Studio-Installer, und suchen Sie den **Boost.Test-Adapter** in der Liste der Workloadkomponenten:

![Installieren von Boost.Test](media/cpp-boost-component.png "Boost.Test für C++ installieren")

## <a name="install-boost"></a>Installieren von Boost

 Boost.Test erfordert [Boost](http://www.boost.org/). Wenn Sie Boost noch nicht installiert haben, sollten Sie den vcpkg-Paket-Manager verwenden. 

1. Falls Sie diesen noch nicht installiert haben, holen Sie dies anhand der Schritte unter [vcpkg: Ein C++-Paket-Manager für Windows](/cpp/vcpkg) nach.
2. Führen Sie `vcpkg install boost` aus, um die Boost-Bibliotheken zu installieren.
3. Führen Sie den Befehl `vcpkg integrate install` aus, um Visual Studio mit der Bibliothek zu konfigurieren und Pfade in den Boost-Headern und Binärdateien einzuschließen. 

## <a name="create-a-project-for-your-tests"></a>Erstellen eines Projekts für Ihre Tests
Visual Studio 2017-Version 15.5 enthält keine vorkonfigurierten Testprojekte oder Elementvorlagen für Boost.Test. Aus diesem Grund müssen Sie ein Konsolenanwendungsprojekt erstellen, in dem Ihre Tests gespeichert werden können. Testvorlagen für Boost.Test sollen in eine zukünftige Version von Visual Studio mit aufgenommen werden. 

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten „Projektmappe“ und dann auf **Hinzufügen > Neues Projekt**. 
2. Wählen Sie im linken Bereich **Windows-Desktop** und dann im mittleren Bereich **Windows-Konsolenanwendung** aus. 
3. Benennen Sie das Projekt, und klicken Sie auf **OK**. 

## <a name="add-include-directives"></a>Hinzufügen von include-Anweisungen
Fügen Sie Ihrer CPP-Testdatei alle erforderlichen `#include`-Anweisungen hinzu, um die Typen und Funktionen Ihres Programms für den Testcode sichtbar zu machen. In der Regel befindet sich das Programm in der Ordnerhierarchie eine Ebene darüber. Wenn Sie `#include "../"` eingeben, wird ein IntelliSense-Fenster angezeigt, und Sie können den vollständigen Pfad zur Headerdatei auswählen.

![Hinzufügen von #include-Direktiven](media/cpp-gtest-includes.png "Hinzufügen von include-Anweisungen zur CPP-Testdatei")

Sie müssen mindestens die [Boost.Test-Variante mit einem einzelnen Header](http://www.boost.org/doc/libs/1_48_0/libs/test/doc/html/utf/user-guide/usage-variants/single-header-variant.html) mit `#include <path>/unit_test.hpp` einschließen und `BOOST_TEST_MODULE` definieren. Das folgende Beispiel reicht aus, damit der Test im **Test-Explorer** sichtbar ist:

```cpp
#include "stdafx.h"
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp>
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual();
    BOOST_CHECK(name == mc.GetName());
}
```

## <a name="write-and-run-tests"></a>Schreiben und Ausführen von Tests
Nun können Sie Tests für Boost.Test schreiben und ausführen. Weitere Informationen zu den Test-Makros finden Sie in der [Dokumentation zur Boost.Test-Bibliothek](http://www.boost.org/doc/libs/1_38_0/libs/test/doc/html/index.html). Weitere Informationen zum Ermitteln, Ausführen und Gruppieren Ihrer Tests mithilfe des **Test-Explorers** finden Sie unter [Ausführen von Komponententests mit dem Test-Explorer](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>Siehe auch
[Schreiben von Komponententests für C/C++](writing-unit-tests-for-c-cpp.md)


  







