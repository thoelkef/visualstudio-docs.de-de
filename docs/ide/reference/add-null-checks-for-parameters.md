---
title: Hinzufügen von Überprüfungen auf NULL für alle Parameter
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 573a9e56d3aedd55bc571eaaa363b42a53019566
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "74782342"
---
# <a name="add-null-checks-for-all-parameters"></a>Hinzufügen von Überprüfungen auf NULL für alle Parameter 

Dieses Refactoring gilt für: 

- C# 

**Beschreibung:** Erstellt und fügt `if`-Anweisungen hinzu, die den NULL-Wert aller nicht geprüften Nullable-Parameter überprüfen. 

**Hintergrund:** Sie möchten schnell Überprüfungen auf NULL für alle anwendbaren Methodenparameter hinzufügen.

**Vorteile**: Das Schreiben von Überprüfungen auf NULL für viele Parameter kann zeitaufwändig sein und viele, sich wiederholenden Aufgaben umfassen sein. Die Verwendung dieses Refactorings ist schnell und macht das Programm stabiler.  

## <a name="how-to"></a>Vorgehensweise 

1. Platzieren Sie den Cursor auf einem beliebigen Parameter innerhalb der Methode.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

   ![Schnellaktionen und Refactorings](media/add-null-checks-for-all-parameters.png)
   
3. Wählen Sie die Option, um **Überprüfungen auf NULL für alle Parameter hinzuzufügen**.

   ![Überprüfungen auf NULL für alle Parameter hinzufügen](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Siehe auch 

- [Refactoring](../refactoring-in-visual-studio.md)
