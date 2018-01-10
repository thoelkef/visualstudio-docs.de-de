---
title: "Verwenden von CTest für C++ in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
author: mikeblome
ms.openlocfilehash: 989f2b06df55fd0927863fe7e5603d3d0ec90b06
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2018
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Verwenden von CTest für C++ in Visual Studio
CMake (schließt CTest mit ein) ist als Standardkomponente der Workload **Desktopentwicklung mit C++** in die Visual Studio-IDE integriert. Öffnen Sie den Visual Studio-Installer, und suchen Sie nach [CMake Tools für Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) in der Liste der Workloadkomponenten, um die Workload auf Ihrem Computer zu installieren.

Die CMake-Unterstützung in Visual Studio umfasst nicht das Visual Studio-Projektsystem. Aus diesem Grund können Sie CTest-Tests auf dieselbe Weise wie in einer CMake-Umgebung schreiben und konfigurieren. Weitere Informationen zu CMake in Visual Studio finden Sie unter [CMake Tools für Visual C++](/cpp/ide/cmake-tools-for-visual-cpp).

Für **Visual Studio 2017 Version 15.5** ist CTest derzeit nicht in den **Test-Explorer** integriert. Sie können Ihre Tests über das CMake-Hauptmenü oder über das Kontextmenü in einer **CMakeLists.txt**-Datei im **Projektmappen-Explorer** ausführen. Die Testergebnisse werden an das Visual Studio-**Ausgabefenster** weitergeleitet.

![CTest-Tests ausführen](media/cpp-cmake-run-tests.png "Run CTest tests")


## <a name="see-also"></a>Siehe auch
[Schreiben von Komponententests für C/C++](writing-unit-tests-for-c-cpp.md)


  







