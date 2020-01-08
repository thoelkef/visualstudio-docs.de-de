---
title: Konvertieren einer Get-Methode in eine Eigenschaft und Konvertieren einer Eigenschaft in eine Get-Methode
ms.date: 01/26/2018
ms.topic: reference
ms.devlang: csharp
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 6e3807f3902cbd0d2718f249f15cd268fb81ac51
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75570231"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Konvertieren einer Get-Methode in eine Eigenschaft und Konvertieren einer Eigenschaft in ein Refactoring einer Get-Methode

Diese Refactorings gelten für:

- C#

## <a name="convert-get-method-to-property"></a>Konvertieren einer Get-Methode in eine Eigenschaft

**Beschreibung:** Hiermit können Sie eine Get-Methode in eine Eigenschaft (und optional die Set-Methode) konvertieren.

**Hintergrund:** Sie verwenden eine Get-Methode, die keinerlei Logik aufweist.

### <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor in den Namen der Get-Methode.

1. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
      - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Replace method with property** (Methode durch Eigenschaft ersetzen) aus.
   - **Maus**
      - Klicken Sie mit der rechten Maustaste auf den Code, und klicken Sie auf das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Replace method with property** (Methode durch Eigenschaft ersetzen) aus.

1. (Optional) Wenn Sie eine Set-Methode verwenden, können Sie diese auch konvertieren, indem sie die **Get-Methode und die Set-Methode durch die Eigenschaft ersetzen**.

1. Wenn Sie mit der Änderung in der Codevorschau zufrieden sind, drücken Sie die **EINGABETASTE**. Die Änderungen werden angewendet. Klicken Sie alternativ im Menü auf die Schaltfläche zum Korrigieren.

Beispiel:

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

## <a name="convert-property-to-get-method"></a>Konvertieren einer Eigenschaft in eine Get-Methode

**Beschreibung:** Hiermit können Sie eine Eigenschaft in eine Get-Methode konvertieren.

**Hintergrund:** Sie verwenden eine Eigenschaft, die mehr als das sofortige Festlegen und Abrufen eines Werts erfordert.

### <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor in den Namen der Get-Methode.

1. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
      - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Eigenschaft durch Methoden ersetzen** aus.
   - **Maus**
      - Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Eigenschaft durch Methoden ersetzen** aus.

1. Wenn Sie mit der Änderung in der Codevorschau zufrieden sind, drücken Sie die **EINGABETASTE**. Die Änderungen werden angewendet. Klicken Sie alternativ im Menü auf die Schaltfläche zum Korrigieren.

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)
