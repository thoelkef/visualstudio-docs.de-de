---
title: Extrahieren einer lokalen Funktion
description: Wandeln Sie ein Codefragment in eine eigene Methode um, indem Sie den Code auswählen und STRG+R, STRG+M drücken.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 031fbe22ec61837d489df7a6af923ef0cd2454c7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "77519326"
---
# <a name="extract-local-function-refactoring"></a>Refactoring des Extrahierens einer lokalen Funktion

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Hiermit können Sie ein Codefragment aus einer vorhandenen Methode in eine lokale Funktion konvertieren.

**Hintergrund:** Wenn Sie über ein vorhandenes Codefragment in einer Methode verfügen, die von einer lokalen Funktion aufgerufen werden muss.

**Vorteile**: Sie könnten diesen Code kopieren und einfügen, dies würde jedoch zu einer Duplizierung führen. Eine bessere Lösung besteht darin, dieses Fragment in eine eigene lokale Funktion umzugestalten.

## <a name="how-to"></a>Vorgehensweise

1. Markieren Sie den zu extrahierenden Code.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen. 

3. Klicken Sie auf **Lokale Funktion extrahieren**.

    ![Extrahieren einer lokalen Funktion](media/extract-local-function.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)
