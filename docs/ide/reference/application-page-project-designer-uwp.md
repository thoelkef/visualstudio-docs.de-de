---
title: Seite der Anwendungseigenschaften für UWP-Apps | Microsoft-Dokumentation
ms.date: 01/23/2018
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- AppPackage.Properties.Application"
helpviewer_keywords:
- Application page [UWP project]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 691a4d2c367bb8f283c4381629f33529fa743c62
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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

Informationen zur Auswahl der Zielplattform in Visual Studio 2017 finden Sie unter [Zielplattformen](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs#a-iddevelopwindows-avisual-studio-2017-support-for-windows-development).

## <a name="see-also"></a>Siehe auch

[Erstellen Ihrer ersten UWP-App](/windows/uwp/get-started/your-first-app)  
[Auswählen einer UWP-Version](/windows/uwp/updates-and-versions/choose-a-uwp-version)