---
title: 'Vorgehensweise: Ändern des Namespace einer domänenspezifischen Sprache'
ms.date: 10/31/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b64a61c02f44db0ce70b758331d0d70f7bb8014d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653767"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Vorgehensweise: Ändern des Namespace einer domänenspezifischen Sprache

Sie können den Namespace einer domänenspezifischen Sprache ändern. Nehmen Sie die Änderung im **DSL-Explorer**, in den Eigenschaften des DSL-Paket Projekts und in den Assemblyinformationen vor.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>So ändern Sie den Namespace einer domänenspezifischen Sprache

1. Wählen Sie im **DSL-Explorer**den Knoten **DSL** aus.

2. Ändern Sie im **Eigenschaften** Fenster die Eigenschaft **Namespace** .

3. Speichern Sie die Projekt Mappe, und transformieren Sie die Vorlagen.

4. Wählen Sie im Menü **Projekt** die Option **DSL-Eigenschaften**aus.

   Die Eigenschaften für das Projekt werden angezeigt.

5. Wählen Sie die Registerkarte **Anwendung** aus.

6. Ändern Sie die Eigenschaft **Standard Namespace** in den neuen Namespace Namen.

7. Wenn Sie auch den Namen der Assembly ändern möchten, ändern Sie die **Eigenschaft AssemblyName.**

8. Wenn Sie den Assemblynamen geändert haben, öffnen Sie dslpackage\package.tt, und aktualisieren Sie diese Zeile:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Wenn Sie benutzerdefinierten Code geschrieben haben, stellen Sie sicher, dass Sie den Namespace und die Klassen Verweise in den Code Dateien ändern.

10. Setzen Sie die experimentelle Instanz von Visual Studio zurück.

    1. Löschen Sie **\Users \\** _{Your Name}_ **\appdata\local\microsoft\visualstudio \\ \*Exp**.

    2. Wählen Sie im Windows- **Startmenü** **Alle Programme**  > **Microsoft Visual Studio 2010 SDK**  > **Tools**  > **die experimentelle Instanz zurücksetzen**.

11. Wählen Sie im Menü **Erstellen** die Option Projekt Mappe **neu erstellen**aus.

## <a name="see-also"></a>Siehe auch

[Glossar für domänenspezifische Sprach Tools](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)