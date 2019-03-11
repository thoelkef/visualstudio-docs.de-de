---
title: Seite der Anwendungseigenschaften für UWP-Apps
ms.date: 01/23/2018
ms.topic: reference
f1_keywords:
- AppPackage.Properties.Application
helpviewer_keywords:
- Application page [UWP project]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 416661a39f54429f24cca66a0ec1be7b6c87629d
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/01/2019
ms.locfileid: "57222713"
---
# <a name="application-property-page-uwp-projects"></a>Eigenschaftenseite der Anwendung (UWP-Projekte)

Verwenden Sie die Eigenschaftenseite **Anwendung**, um die Assembly- und Paketinformationen für das UWP-Projekt (Universal Windows Platform, universelle Windows-Plattform) anzugeben und Windows 10 als Zielversion festzulegen.

![Eigenschaftenseite der Anwendung](media/application-page-uwp.png)

Um auf die Seite **Anwendung** zuzugreifen, wählen Sie im **Projektmappen-Explorer** den Projektknoten aus. Wählen Sie dann in der Menüleiste **Projekt** > **Eigenschaften** aus. Die Eigenschaftenseiten werden auf der Registerkarte **Anwendung** geöffnet.

## <a name="general-section"></a>Abschnitt „Allgemein“

**Assemblyname**: Gibt den Namen der Ausgabedatei an, in der das Assemblymanifest enthalten ist.

Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Standardnamespace**: Legt den Basisnamespace für Dateien fest, die dem Projekt hinzugefügt werden. Weitere Informationen zu Namespaces finden Sie unter [Namespace (C#-Programmierhandbuch)](/dotnet/csharp/programming-guide/namespaces/), [Namespaces (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces) oder [Namespaces (C++)](/cpp/cpp/namespaces-cpp).

Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Assemblyinformationen**: Durch Klicken auf diese Schaltfläche wird das Dialogfeld [Assemblyinformationen](../../ide/reference/assembly-information-dialog-box.md) angezeigt.

**Paketmanifest**: Durch Klicken auf diese Schaltfläche wird der Manifest-Designer geöffnet. Auf den Manifest-Designer können Sie auch durch Auswählen der Datei _Package.appxmanifest_ im **Projektmappen-Explorer** zugreifen. Weitere Informationen finden Sie unter [Konfigurieren einen Pakets mit dem Manifest-Designer](/windows/uwp/packaging/packaging-uwp-apps#configure-an-app-package).

## <a name="targeting-section"></a>Bereich „Ziel“

Sie können die Zielversion und die Mindestversion von Windows 10 für Ihre App mithilfe der Dropdownlisten in diesem Abschnitt festlegen. Es wird empfohlen, die neueste Version von Windows 10 als Ziel zu verwenden. Wenn Sie eine Unternehmens-App entwickeln, sollten Sie außerdem eine ältere Mindestversion unterstützen. Weitere Informationen zur Auswahl der Windows 10-Version finden Sie unter [Auswählen einer UWP-Version](/windows/uwp/updates-and-versions/choose-a-uwp-version).

Informationen zur Auswahl der Zielplattform in Visual Studio finden Sie unter [Zielplattformen](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting).

## <a name="see-also"></a>Siehe auch

- [Erstellen Ihrer ersten UWP-App](/windows/uwp/get-started/your-first-app)
- [Auswählen einer UWP-Version](/windows/uwp/updates-and-versions/choose-a-uwp-version)