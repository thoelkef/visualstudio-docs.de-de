---
title: Importieren eines XCode-Projektes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
ms.technology: vs-ide-mobile
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 500dce15e695cf53a061f8405919e808b8f7c493
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31066937"
---
# <a name="import-an-xcode-project"></a>Importieren eines XCode-Projekts
Microsoft Visual C++ für die plattformübergreifende, mobile Entwicklung umfasst die Unterstützung für das Verschieben von XCode-Projekten in Visual Studio, in dem Sie plattformübergreifende Bibliotheken erstellen und den Code mit anderen Projekten nutzen können. Der „Aus XCode importieren“-Assistent vereinfacht den Prozess des Importierens von Projekten und des Aufteilens des C++-Codes auf Ihre XCode-Ziele, um diese als eine statische Bibliothek oder ein freigegebenes Codeprojekt zu verwenden. Sie können Ihren iOS-spezifischen Code in Visual Studio verwalten und trotzdem XCode verwenden, um Storyboards und Builds auszuführen. Informationen darüber, wie Sie einfach Code zwischen Visual Studio und XCode verschieben können, finden Sie unter „Änderungen zwischen XCode und Visual Studio“.  
  
## <a name="using-the-import-from-xcode-wizard"></a>Verwenden des „Aus XCode importieren“-Assistenten  
 Hier erfahren Sie, wie Sie ein XCode-Projekt in Visual Studio verschieben, um von Codefreigaben und plattformübergreifende Lösungen zu profitieren. Als Vorbereitungsmaßnahme müssen Sie Ihren Mac mit Visual Studio koppeln, um Ihr Projekt importieren, exportieren und erstellen zu können. Ausführliche Anweisungen zur Kopplung finden Sie unter [Installieren und Konfigurieren von Tools zum Erstellen mit iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Außerdem müssen Sie Ihr XCode-Projekt über das Netzwerk freigeben oder es auf Ihren Computer, auf dem Visual Studio installiert ist, verschieben, um den „Aus XCode importieren“-Assistenten zu verwenden.  
  
#### <a name="import-from-xcode"></a>Importieren aus XCode  
  
1.  Wählen Sie im Menü **Datei** die Optionen **Neu**, **Importieren** **Aus XCode importieren** aus. Dadurch wird das **Aus XCode importieren**-Dialogfeld für den Assistenten gestartet.  
  
     ![Auswählen des zu importierenden XCode-Zielprojekts](../cross-platform/media/cppmdd_u2_importxcode_choose.PNG "CPPMDD_U2_ImportXCode_Choose")  
  
2.  Wählen Sie im Bereich **Ein Projekt auswählen** die Schaltfläche „Browser“ aus, um eine XCode PBXPROJ-Datei auszuwählen. Navigieren Sie zu der Projektdatei im Dialogfeld **XCode-Projektdatei auswählen**, und wählen Sie anschließend **Öffnen** aus.  
  
     ![Auswählen einer Projektdatei im Dialogfeld „XCode-Projektdatei auswählen“](../cross-platform/media/cppmdd_u2_importxcode_browse.PNG "CPPMDD_U2_ImportXCode_Browse")  
  
     Wählen Sie im „Aus XCode importieren“-Assistenten **Weiter** aus.  
  
3.  Wählen Sie im Bereich **Ziele** die Ziele des XCode-Projekts, die in die Visual Studio-Projekte importiert werden sollen. XCode-Ziele ähneln den Visual Studio-Projekten. Die meisten sind eine Sammlung von Code und Ressourcen, die eine Binärdatei erzeugen. Der „Aus XCode importieren“-Assistent ermöglicht nur das Importieren der Ziele, die eine Binärdatei, aber keine statische Bibliothek als Ziele erzeugen. Statische Bibliotheksziele mit Xcode sind Gegenstand des nächsten Schritts.  
  
     ![Zielbereich des „Aus XCode importieren“-Assistenten](../cross-platform/media/cppmdd_u2_importxcode_destination.jpg "CPPMDD_U2_ImportXCode_Destination")  
  
     Für jedes Ziel, das unter **Zu importierende Ziele** ausgewählt wurde, erkennt der Assistent automatisch C++-Codedateien, die in einem separaten statischen Bibliotheksprojekt aufgeteilt werden können, und fügt sie im Abschnitt **C++-Projektelemente** hinzu. Andere Codes und Ressourcen verbleiben im Abschnitt **XCode-Projektelemente**. Diese werden nach Abschluss des Importprozesses durch den Assistenten zu separaten statischen Bibliotheks- und Anwendungsprojekten in Visual Studio. Standardmäßig werden Komponententest- und Frameworkziele vom Assistenten nicht in separate Projekte aufgeteilt.  
  
     Verwenden Sie die Schaltflächen „nach oben“ und „nach unten“, um zu ändern, welche Dateien sich in jedem Projekt befinden. Wenn Sie mit den Dateien in jedem Projekt zufrieden sind, wählen Sie **Weiter** aus, um den Vorgang fortzusetzen.  
  
4.  Wählen Sie Im Bereich **Bibliotheksziel** die statischen Bibliotheksziele des XCode-Projekts aus, die in die Visual Studio-Projekte importiert werden sollen. In diesem Bereich können Sie auswählen, welche Dateien in einem Projekt mit freigegebenem Code eingefügt werden, und welche in einem statischen Bibliotheksprojekt platziert werden. In jedem der Ziele in der Liste **Zu importierende Ziele** können Sie mithilfe der Schaltflächen „nach oben“ und „nach unten“ steuern, welche Dateien in den **Elementen für Projekte mit freigegebenem Code** und den **Projektelementen der statischen Bibliothek** platziert werden.  
  
     ![Bibliothekszielbereich „Aus XCode importieren“](../cross-platform/media/cppmdd_u2_importxcode_library.jpg "CPPMDD_U2_ImportXCode_Library")  
  
     Ein Projekt mit freigegebenem Code bietet eine Möglichkeit zur Freigabe eines Satzes von Quellcodedateien für unterschiedliche Projekte in Visual Studio. Der Code wird als Teil des Projekts erstellt, das ihn enthält, und nicht als eigenes Projekt. Da die Projekte, die den freigegebenen Code enthalten, unterschiedliche Architekturen und Konfigurationen haben können, ist dies die beste Möglichkeit, ein einzelnes Projekt bereitzustellen, das Code enthält, der für viele Arten von Plattformen erstellt werden kann.  
  
     Wenn Sie mit den Dateien in jedem Projekt zufrieden sind, wählen Sie **Weiter** aus, um den Vorgang fortzusetzen.  
  
5.  Der Bereich **Globale Eigenschaften** kann verwendet werden, um einen Framework-Suchpfad und einen Suchpfad zum Einschließen von Headern für alle iOS-Projekte in Visual Studio festzulegen. Visual Studio verwendet diese Pfade für das Durchsuchen von Quellcode und für IntelliSense. Diese globalen Pfade sind nützlich, wenn Sie iOS-Projekte erstellen, die einen gemeinsamen Satz von Headern und Frameworks verwenden.  
  
     ![„Globale Eigenschaften“-Bereich „Aus XCode importieren“](../cross-platform/media/cppmdd_u2_importxcode_global.jpg "CPPMDD_U2_ImportXCode_Global")  
  
     Diese globalen Pfade können auch in Visual Studio im Dialogfeld **Optionen** festgelegt werden. Wählen Sie im Menü **Tools** **Optionen** aus, um sie zu finden. Im Dialogfeld **Optionen**, erweitern Sie **Plattformübergreifend**, **C++**, **iOS** und **Globale Eigenschaften**.  
  
     Klicken Sie auf **Weiter** , um fortzufahren.  
  
6.  Der Bereich **Frameworks** wird verwendet, um die von Visual Studio zum Durchsuchen verwendeten Pfade und IntelliSense für Ihr Projekt zu konfigurieren. Die Pfade müssen für Visual Studio für jedes Framework zugänglich sein, auf das Ihr XCode-Projekt verweist. Der Assistent überprüft die Frameworkverweise in den XCode-Projekten und zeigt an, ob Visual Studio das Framework finden kann. Jeder Pfad, den Sie bereits in den globalen Eigenschaften eingerichtet haben, sollte von Visual Studio erkannt werden. Die Ausnahmen werden in der Liste der Frameworks aufgeführt. Stellen Sie für jedes aufgelistete Framework mit einem X einen vom PC zugänglichen Pfad für Visual Studio bereit, um das Framework zu finden. Sie können die Schaltfläche zum Durchsuchen „[...]“, verwenden, um das Dialogfeld **Ordner auswählen** zum Suchen des Pfads zu nutzen. Der Frameworkpfad kann entweder auf eine lokale Kopie oder eine Freigabe verweisen, auf die über das Netzwerk auf Ihrem Mac zugegriffen werden kann.  
  
     ![„Framework“-Bereich „Aus XCode importieren“ ](../cross-platform/media/cppmdd_u2_importxcode_frameworks.jpg "CPPMDD_U2_ImportXCode_Frameworks")  
  
     Klicken Sie auf **Weiter** , um fortzufahren.  
  
7.  Der Bereich **Projekteinstellungen** erlaubt es Ihnen, das Framework zu ändern, und beinhaltet Einstellungen für den Suchpfad für Header für jedes Projekt, das der Assistent erstellt. Verwenden Sie diesen Bereich, um projektspezifische Pfade, die sich von den globalen Einstellungen unterscheiden, festzulegen.  
  
     Um einen Pfad für ein bestimmtes Projekt festzulegen, wählen Sie im Dropdownmenü **Zielprojekt** die Projektdatei aus, legen Sie anschließend die Werte in den Steuerelementen **Framework-Suchpfad** und **Suchpfad für Header einbeziehen** fest. Sie können die Schaltfläche zum Durchsuchen „[...]“ neben jedem Steuerelement verwenden, um das Dialogfeld **Ordner auswählen** zum Suchen des Pfads zu nutzen.  
  
     ![Bereich „Importieren aus XCode-Projekten“](../cross-platform/media/cppmdd_u2_importxcode_projects.jpg "CPPMDD_U2_ImportXCode_Projects")  
  
     Wenn dieser PC in Visual Studio keinem remoten Mac-Computer zugeordnet wurde, wird der Link „Remotecomputer konfigurieren“ angezeigt. Ausführliche Anweisungen zur Kopplung finden Sie unter [Installieren und Konfigurieren von Tools zum Erstellen mit iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
     Wählen Sie **Importieren** aus, um das XCode-Projekt mithilfe der Einstellungen des Assistenten zu importieren.  
  
 Der „Aus XCode importieren“-Assistent erstellt Projekte in Visual Studio, die den ausgewählten XCode-Projektzielen entsprechen. Der Code, der mit anderen C++-Projekten gemeinsam genutzt werden kann, wird in einen separat freigegebenen Code und statische Bibliotheksprojekte unterteilt. Der restliche Code wird in den iOS-Bibliotheks- und Anwendungsprojekten eingefügt, die von Visual Studio remote erstellt werden können. Weitere Informationen zum Verschieben von Code zwischen Visual Studio und XCode finden Sie unter [Synchronisierungsänderungen zwischen XCode und Visual Studio](../cross-platform/sync-changes-between-xcode-and-visual-studio.md).