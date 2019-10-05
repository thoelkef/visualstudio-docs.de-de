---
title: Für das Konvertieren einer lokalen Funktion in eine Methode.
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3572682fe68d9b0b1bc4adee537de5cd056a8906
ms.sourcegitcommit: 9a3972eb85de5443ac2bc03964c5a251c39b2921
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2019
ms.locfileid: "71301694"
---
# <a name="convert-a-local-function-to-a-method"></a>Für das Konvertieren einer lokalen Funktion in eine Methode.

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Für das Konvertieren einer lokalen Funktion in eine Methode.

**Hintergrund:** Sie haben eine lokale Funktion, die Sie außerhalb Ihres aktuellen lokalen Kontexts definieren möchten.

**Vorteile**: Sie sollten eine lokale Funktion in eine Methode konvertieren, damit Sie sie außerhalb Ihres lokalen Kontexts aufrufen können. Sie sollten sie auch in eine Methode konvertieren, wenn Ihre lokale Funktion zu lang wird. Wenn Sie die Funktion in einer separaten Methode definieren, ist Ihr Code besser lesbar.

## <a name="convert-local-function-to-method-refactoring"></a>Konvertieren von lokalen Funktionen in Methodenrefactoring

1. Platzieren Sie Ihren Cursor auf einer lokalen Funktion.

    ![Konvertieren einer lokalen Funktion in einen Methodencode – Beispiel](media/convert-local-function-to-method.png)

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

    ![Konvertieren einer lokalen Funktion in einen Methoden-Codefix – Beispiel](media/convert-local-function-to-method-codefix.png)

2. Drücken Sie die Eingabetaste, um das Refactoring zu akzeptieren.

    ![Konvertieren einer lokalen Funktion in ein Methodenergebnis – Beispiel](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipps für .NET-Entwickler](../csharp-developer-productivity.md)
