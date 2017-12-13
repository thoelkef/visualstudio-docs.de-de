---
title: "Verwenden von CTest für C++ in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8b30934-5f38-4a18-8819-263e0733cdbe
caps.latest.revision: "14"
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7e1d00460a4acf26f23c256f8eb0180360315a98
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2017
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Verwenden von CTest für C++ in Visual Studio
CMake (schließt CTest mit ein) ist als Standardkomponente der Workload **Desktopentwicklung mit C++** in die Visual Studio-IDE integriert. Öffnen Sie den Visual Studio-Installer, und suchen Sie nach [CMake Tools für Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) in der Liste der Workloadkomponenten, um die Workload auf Ihrem Computer zu installieren.

Die CMake-Unterstützung in Visual Studio umfasst nicht das Visual Studio-Projektsystem. Aus diesem Grund können Sie CTest-Tests auf dieselbe Weise wie in einer CMake-Umgebung schreiben und konfigurieren. Weitere Informationen zu CMake in Visual Studio finden Sie unter [CMake Tools für Visual C++](/cpp/ide/cmake-tools-for-visual-cpp).

Für **Visual Studio 2017 Version 15.5** ist CTest derzeit nicht in den **Test-Explorer** integriert. Sie können Ihre Tests über das CMake-Hauptmenü oder über das Kontextmenü in einer **CMakeLists.txt**-Datei im **Projektmappen-Explorer** ausführen. Die Testergebnisse werden an das Visual Studio-**Ausgabefenster** weitergeleitet.

![CTest-Tests ausführen](media/cpp-cmake-run-tests.png "Run CTest tests")


## <a name="see-also"></a>Siehe auch
[Schreiben von Komponententests für C/C++](writing-unit-tests-for-c-cpp.md)


  







