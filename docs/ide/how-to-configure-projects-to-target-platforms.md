---
title: 'Vorgehensweise: Konfigurieren von Projekten für Zielplattformen'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: faef9f55a88385953a121574f761193cc8c11ea9
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416822"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Vorgehensweise: Konfigurieren von Projekten für Zielplattformen

Visual Studio ermöglicht es Ihnen, die Anwendungen für unterschiedliche Zielplattformen einzurichten, einschließlich 64-Bit-Plattformen. Weitere Informationen zur Unterstützung von 64-Bit-Plattformen in Visual Studio finden Sie unter [64-Bit-Anwendungen](/dotnet/framework/64-bit-apps).

## <a name="target-platforms-with-the-configuration-manager"></a>Zielplattformen mit dem Konfigurations-Manager

Mit dem **Konfigurations-Manager** können Sie für ein Projekt schnell eine neue Zielplattform hinzufügen. Wenn Sie eine der in Visual Studio enthaltenen Plattformen auswählen, werden die Projekteigenschaften geändert, um das Projekt unter Berücksichtigung der ausgewählten Plattform zu erstellen.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>So konfigurieren Sie ein Projekt für eine 64-Bit-Plattform

1. Klicken Sie in der Menüleiste auf **Build** > **Konfigurations-Manager**.

2. Wählen Sie in der Liste **Aktive Projektmappenplattform** eine 64-Bit-Plattform als Zielplattform für die Projektmappe aus, und klicken Sie dann auf die Schaltfläche **Schließen**.

    1. Wählen Sie **Neu** aus, wenn die gewünschte Plattform nicht in der Liste **Aktive Projektmappenplattform** angezeigt wird.

         Das Dialogfeld **Neue Projektmappenplattform** wird angezeigt.

    2. Wählen Sie in der Liste **Neue Plattform eingeben oder auswählen** **x64** aus.

        > [!NOTE]
        > Wenn Sie die Konfiguration neu benennen, müssen Sie möglicherweise die Einstellungen für die gewünschte Zielplattform im **Projekt-Designer** konfigurieren.

    3. Wenn Sie die Einstellungen aus der aktuellen Plattformkonfiguration kopieren möchten, wählen Sie diese aus, und wählen Sie anschließend die Schaltfläche **OK** aus.

Es werden die Eigenschaften für alle Projekte mit der 64-Bit-Plattform als Zielplattform aktualisiert, und der nächste Build des Projekts wird für 64-Bit-Plattformen optimiert.

## <a name="target-platforms-in-the-project-designer"></a>Zielplattformen im Projekt-Designer

Mit dem **Projekt-Designer** können Sie ebenfalls unterschiedliche Zielplattformen für Ihr Projekt festlegen. Wenn Sie die gewünschte Zielplattform nicht in der Liste im Dialogfeld **Neue Projektmappenplattform** auswählen können, können Sie eine benutzerdefinierte Konfiguration erstellen und benennen und die Einstellungen für die gewünschte Zielplattform im **Projekt-Designer** konfigurieren.

Die für diese Aufgabe erforderlichen Schritte sind je nach Programmiersprache unterschiedlich. Weitere Informationen finden Sie unter den folgenden Links:

- Informationen zu -[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]Projekten finden Sie unter [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

- Informationen zu [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Projekten finden Sie unter [Seite „Erstellen“, Projekt-Designer (C#)](../ide/reference/build-page-project-designer-csharp.md).

- Informationen zu [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]-Projekten finden Sie unter [/clr (Common Language Runtime-Kompilierung)](/cpp/build/reference/clr-common-language-runtime-compilation).

## <a name="see-also"></a>Siehe auch

- [Grundlagen zu Buildplattformen](../ide/understanding-build-platforms.md)
- [/platform (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [64-Bit-Anwendungen](/dotnet/framework/64-bit-apps)
- [Visual Studio-IDE-64-Bit-Unterstützung](../ide/visual-studio-ide-64-bit-support.md)
