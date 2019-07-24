---
title: 'Vorgehensweise: Ändern des Buildausgabeverzeichnisses'
ms.date: 05/15/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e006be2099d5132ce7445f1e8fe74b0f2752c260
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416814"
---
# <a name="how-to-change-the-build-output-directory"></a>Vorgehensweise: Ändern des Buildausgabeverzeichnisses

Sie können den Speicherort der von Ihrem Projekt generierten Ausgabe auf Basis der Konfiguration („Debug“, „Release“ oder beides) angeben.

## <a name="change-the-build-output-directory"></a>Ändern des Buildausgabeverzeichnisses

1. Navigieren Sie zur Seite mit den Projekteigenschaften. Klicken Sie hierzu im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eigenschaften** aus.

2. Wählen Sie basierend auf Ihren Projekttyp die entsprechende Registerkarte:

   - Wählen Sie für C# die Registerkarte **Erstellen** aus.
   - Wählen Sie für Visual Basic die Registerkarte **Kompilieren** aus.
   - Wählen Sie für C++ oder JavaScript die Registerkarte **Allgemein**.

3. Wählen Sie in der Konfigurationen-Dropdownliste am oberen Rand die Konfiguration aus, deren Speicherort der Ausgabedatei Sie ändern möchten (**Debug**, **Release** oder **Alle Konfigurationen**).

4. Suchen Sie auf der Seite den Eintrag des Ausgabepfads. Er unterscheidet sich je nach Projekttyp:

   - **Ausgabepfad** für C#- und JavaScript-Projekte
   - **Buildausgabepfad** für Visual Basic-Projekte
   - **Ausgabeverzeichnis** für Visual C++-Projekte

   Geben Sie den Pfad zum Generieren der Ausgabe (absolut oder relativ zum Stammverzeichnis des Projekts) ein, oder wählen Sie **Durchsuchen**, um stattdessen zu diesem Ordner zu navigieren.

   ![Ausgabepfadeigenschaft für ein Visual Studio C#-Projekt](media/output-path.png)

> [!TIP]
> Wenn die Ausgabe nicht an dem festgelegten Speicherort generiert wird, müssen Sie in der Menüleiste von Visual Studio die entsprechende Konfiguration (z. B. **Debuggen** oder **Version**) erstellen.
>
> ![Auswahl der Buildkonfiguration in Visual Studio 2019](media/build-configuration-chooser.png)

## <a name="see-also"></a>Siehe auch

- [Seite „Erstellen“, Projekt-Designer (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [Allgemeine Eigenschaftenseite (Projekt)](/cpp/build/reference/general-property-page-project)
- [Kompilieren und Erstellen](../ide/compiling-and-building-in-visual-studio.md)