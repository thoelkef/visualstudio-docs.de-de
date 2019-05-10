---
title: 'Vorgehensweise: Ändern Sie den Namespace einer domänenspezifischen Sprache'
ms.date: 10/31/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16fec4cf6150fe0711812d9fabe57fc667e36eef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993499"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Vorgehensweise: Ändern Sie den Namespace einer domänenspezifischen Sprache

Sie können den Namespace einer domänenspezifischen Sprache ändern. Nehmen Sie die Änderung in der **DSL-Explorer**, in den Eigenschaften des Projekts Dsl-Paket und die Assembly-Informationen.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>So ändern Sie den Namespace einer domänenspezifischen Sprache

1. In **DSL-Explorer**, wählen die **Dsl** Knoten.

2. In der **Eigenschaften** Ändern der **Namespace** Eigenschaft.

3. Speichern Sie die Projektmappe, und Transformieren Sie die Vorlagen zu.

4. Auf der **Projekt** Menü wählen **Dsl Eigenschaften**.

   Die Eigenschaften für das Projekt angezeigt werden.

5. Wählen Sie die **Anwendung** Registerkarte.

6. Ändern der **Standardnamespace** Eigenschaft, um den neuen Namespacenamen.

7. Wenn Sie auch den Namen der Assembly ändern möchten, ändern Sie die **Assemblyname (Eigenschaft).**

8. Wenn Sie den Assemblynamen geändert haben, öffnen Sie DslPackage\Package.tt, und aktualisieren Sie diese Zeile:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Wenn Sie keinen benutzerdefinierten Code geschrieben haben, stellen Sie sicher, dass die Namespace- und Klassennamen Verweise in den Codedateien zu ändern.

10. Setzen Sie die experimentelle Instanz Visual Studio zurück.

    1. Löschen Sie **\Users\\**_{Ihr Name}_**\AppData\Local\Microsoft\VisualStudio\\\*"exp"**.

    2. Auf der Windows **starten** Menü wählen **Programme** > **Microsoft Visual Studio 2010 SDK** > **Tools**  >  **Zurücksetzen die experimentelle Instanz**.

11. Auf der **erstellen** Menü wählen **Projektmappe neu erstellen**.

## <a name="see-also"></a>Siehe auch

[DSL-Tools – Glossar](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)