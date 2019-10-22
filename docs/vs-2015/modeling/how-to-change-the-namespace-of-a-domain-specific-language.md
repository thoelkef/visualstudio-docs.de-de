---
title: 'Vorgehensweise: Ändern des Namespace einer domänenspezifischen Sprache | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8b61b248876f701e9d5286063f28b4f71d73e18b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671723"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Gewusst wie: Ändern des Namespace einer domänenspezifischen Sprache
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können den Namespace einer domänenspezifischen Sprache ändern. Sie müssen die Änderung im DSL- **Explorer**, in den Eigenschaften des DSL-Paket Projekts und in den Assemblyinformationen vornehmen.

### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>So ändern Sie den Namespace einer domänenspezifischen Sprache

1. Klicken Sie im **DSL-Explorer**auf den Knoten **DSL** .

2. Ändern Sie im **Eigenschaften** Fenster die Eigenschaft **Namespace** .

3. Speichern Sie die Projekt Mappe, und transformieren Sie die Vorlagen.

4. Klicken Sie im Menü **Projekt** auf **DSL-Eigenschaften**.

     Die Eigenschaften für das Projekt werden angezeigt.

5. Klicken Sie auf die Registerkarte **Anwendung** .

6. Ändern Sie die Eigenschaft **Standard Namespace** in den neuen Namespace Namen.

7. Wenn Sie auch den Namen der Assembly ändern möchten, ändern Sie die **Eigenschaft AssemblyName.**

8. Wenn Sie den Assemblynamen geändert haben, öffnen Sie dslpackage\package.tt, und aktualisieren Sie diese Zeile:

     `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Wenn Sie benutzerdefinierten Code geschrieben haben, stellen Sie sicher, dass Sie den Namespace und die Klassen Verweise in den Code Dateien ändern.

10. Setzen Sie die experimentelle Instanz von Visual Studio zurück.

    1. Löschen Sie **\Users \\** _{Your Name}_ **\appdata\local\microsoft\visualstudio \\ \*Exp**

    2. Wählen Sie im Windows- **Startmenü** **Alle Programme**, **Microsoft Visual Studio 2010 SDK**, **Tools**und **die experimentelle Instanz zurücksetzen**aus.

11. Wählen Sie im Menü **Erstellen** die Option Projekt Mappe **neu erstellen**aus.

## <a name="see-also"></a>Siehe auch
 [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
