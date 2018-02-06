---
title: Konvertieren einer Get-Methode in eine Eigenschaft und Konvertieren einer Eigenschaft in eine Get-Methode in C# | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
f1_keywords: vs.csharp.refactoring.convertmethodtoproperty
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: a23af31c5099908ed0b6fed07404216a57975f75
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="convert-get-method-to-property--convert-property-to-get-method"></a>Konvertieren einer Get-Methode in eine Eigenschaft und Konvertieren einer Eigenschaft in eine Get-Methode

## <a name="convert-get-method-to-property"></a>Konvertieren einer Get-Methode in eine Eigenschaft

**Beschreibung**: Hiermit können Sie eine Get-Methode in eine Eigenschaft (und optional die Set-Methode) konvertieren und umgekehrt.

**Hintergrund**: Sie verwenden eine Get-Methode, die keinerlei Logik aufweist.

**Vorgehensweise**:

1. Platzieren Sie den Cursor in den Namen der Get-Methode.

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Methode durch Eigenschaft ersetzen** aus. Wenn Sie eine Set-Methode verwenden, können Sie die Set-Methode auch konvertieren, indem sie die **Get-Methode und Set-Methode durch die Eigenschaft ersetzen**.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Methode durch Eigenschaft ersetzen** aus. Wenn Sie eine Set-Methode verwenden, können Sie die Set-Methode auch konvertieren, indem sie die **Get-Methode und Set-Methode durch die Eigenschaft ersetzen**.

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

**Beschreibung**: Hiermit können Sie eine Eigenschaft in eine Get-Methode konvertieren.

**Hintergrund**: Sie verwenden eine Eigenschaft, die mehr als das sofortige Festlegen und Abrufen eines Werts erfordert. 

**Vorgehensweise**:

1. Platzieren Sie den Cursor in den Namen der Get-Methode.

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Eigenschaft durch Methoden ersetzen** aus.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Eigenschaft durch Methoden ersetzen** aus.

1. Wenn Sie mit der Änderung in der Codevorschau zufrieden sind, drücken Sie die **EINGABETASTE**. Die Änderungen werden angewendet. Klicken Sie alternativ im Menü auf die Schaltfläche zum Korrigieren.

## <a name="see-also"></a>Siehe auch

[Refactoring](../refactoring-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)