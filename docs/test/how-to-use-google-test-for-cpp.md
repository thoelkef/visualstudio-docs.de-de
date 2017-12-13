---
title: "Verwenden von Google Test für C++ in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4868fae-fd6d-4b98-a85f-f23b0dd2fca5
caps.latest.revision: "14"
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4a67fa6e2a9f317643fe63138a4212676606a64d
ms.sourcegitcommit: cc288456329aefca1fdaa7ce74751ce195985c14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2017
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Verwenden von Google Test für C++ in Visual Studio
In **Visual Studio 2017 Version 15.5** und höher wird Google Test als Standardkomponente der Workload **Desktopentwicklung mit C++** in die Visual Studio-IDE integriert. Öffnen Sie den Visual Studio-Installer, und suchen Sie Google Test in der Liste der Workloadkomponenten, um sicherzustellen, dass dieses auf Ihrem Computer installiert ist.

![Installieren von Google Test](media/cpp-google-component.png "Installieren von Google Test für C++")

## <a name="add-a-google-test-project-to-the-solution"></a>Hinzufügen eines Google Test-Projekts zur Projektmappe
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten „Projektmappe“, und klicken Sie auf **Hinzufügen > Neues Projekt**. 
2. Klicken Sie im linken Bereich auf **Visual C++ > Test** und dann auf **Google Test Project** (Google Test-Projekt) im mittleren Bereich. 
3. Benennen Sie das Testprojekt, und klicken Sie auf **OK**. 

![Neues Google-Testprojekt](media/cpp-gtest-new-project.png "Hinzufügen eines neuen Google-Testprojekts")

## <a name="configure-the-test-project"></a>Konfigurieren des Testprojekts
Im Dialogfeld **Testprojektkonfiguration**, das Ihnen angezeigt wird, können Sie das Projekt auswählen, das Sie testen möchten. Wenn Sie ein Projekt auswählen, fügt Visual Studio einen Verweis auf das ausgewählte Projekt hinzu. Wenn Sie kein Projekt auswählen, müssen Sie manuell Verweise auf das Projekt hinzufügen, das Sie testen möchten. Bei der Auswahl zwischen statischer und dynamischer Verknüpfung mit den Google Test-Binärdateien müssen die gleichen Aspekte wie bei jedem anderen C++-Programm beachtet werden. Weitere Informationen finden Sie unter [DLLs in Visual C++](/cpp/build/dlls-in-visual-cpp). 

 ![Konfigurieren von Google Test-Projekten](media/cpp-gtest-config.png "Configure Google Test Project")

## <a name="set-additional-options"></a>Festlegen von zusätzlichen Optionen
Klicken Sie im Hauptmenü auf **Extras > Optionen > Testadapter für Google Test**, um zusätzliche Optionen festzulegen. Weitere Informationen zu diesen Einstellungen finden Sie in der Google Test-Dokumentation.

 ![Google Test-Projekteinstellungen](media/cpp-gtest-settings.png "Google Test Project settings")

## <a name="add-include-directives"></a>Hinzufügen von include-Anweisungen
Fügen Sie Ihrer CPP-Testdatei alle erforderlichen `#include`-Anweisungen hinzu, um die Typen und Funktionen Ihres Programms für den Testcode sichtbar zu machen. In der Regel befindet sich das Programm in der Ordnerhierarchie eine Ebene darüber. Wenn Sie `#include "../"` eingeben, wird ein IntelliSense-Fenster angezeigt, und Sie können den vollständigen Pfad zur Headerdatei auswählen.

![Hinzufügen von #include-Direktiven](media/cpp-gtest-includes.png "Hinzufügen von include-Anweisungen zur CPP-Testdatei")

## <a name="write-and-run-tests"></a>Schreiben und Ausführen von Tests
Sie können nun Google Test-Tests schreiben und ausführen. Weitere Informationen über die Testmakros finden Sie unter [Einführung in Google Test](https://github.com/google/googletest/blob/master/googletest/docs/Primer.md). Weitere Informationen zum Ermitteln, Ausführen und Gruppieren Ihrer Tests mithilfe des **Test-Explorers** finden Sie unter [Ausführen von Komponententests mit dem Test-Explorer](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>Siehe auch
[Schreiben von Komponententests für C/C++](writing-unit-tests-for-c-cpp.md)


  







