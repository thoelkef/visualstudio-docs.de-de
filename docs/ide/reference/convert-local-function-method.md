---
title: Konvertieren von lokalen Funktionen in Methoden
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 96064b16e53081e0456ed43275acd5edf7ead468
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152953"
---
# <a name="convert-local-function-to-method"></a>Konvertieren von lokalen Funktionen in Methoden

Dieses Refactoring gilt für:

- C#
- Visual Basic

**Beschreibung:** Für das Konvertieren einer lokalen Funktion in eine Methode.

**Hintergrund:** Sie haben eine lokale Funktion, die Sie außerhalb Ihres aktuellen lokalen Kontexts definieren möchten.

**Vorteile**: Sie sollten eine lokale Funktion in eine Methode konvertieren, damit Sie sie außerhalb Ihres lokalen Kontexts aufrufen können. Sie sollten sie auch in eine Methode konvertieren, wenn Ihre lokale Funktion zu lang wird. Wenn sie in einer separaten Methode definiert wird, erleichtert dies die Lesbarkeit.

## <a name="convert-local-function-to-method-refactoring"></a>Konvertieren von lokalen Funktionen in Methodenrefactoring

1. Platzieren Sie Ihren Cursor auf einer lokalen Funktion.

    ![Konvertieren von lokalen Funktionen in Methoden](media/convert-local-function-to-method.png)

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.

    ![Konvertieren einer lokalen Funktion in einen Methoden-Codefix](media/convert-local-function-to-method-codefix.png)

2. Drücken Sie die **EINGABETASTE**, um das Refactoring zu akzeptieren.

    ![Konvertieren einer lokalen Funktion in ein Methoden-Ergebnis](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipps für .NET-Entwickler](../../ide/visual-studio-2017-for-dotnet-developers.md)
