---
title: 'Gewusst wie: Aktivieren und Deaktivieren der Pluralisierung (O-R-Designer) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: afe8c8a4429efb83c09d80a5dd00dfe08b0d63e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665936"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Vorgehensweise: Aktivieren/Deaktivieren der Pluralisierung (O/R-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie Datenbankobjekte mit Namen, die in s oder IES enden, von **Server-Explorer** /**Datenbank-Explorer** auf die [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)ziehen, werden die Namen der generierten Entitäts Klassen standardmäßig von Plural in besondere. Damit soll verdeutlicht werden, dass die instanziierte Entitätsklasse einem einzigen Datensatz zugeordnet ist. Wird dem [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] beispielsweise die Tabelle Customers hinzugefügt, erhält die Entitätsklasse den Namen Customer, da die Klasse die Daten eines einzigen Kunden enthält.

> [!NOTE]
> Pluralisierung ist standardmäßig nur in der englischsprachigen Version von Visual Studio aktiviert.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>So schalten Sie Pluralisierung ein und aus

1. Klicken Sie im Menü **Extras** auf **Optionen**.

2. Erweitern Sie im Dialogfeld **Optionen** den Knoten **Datenbanktools**.

> [!NOTE]
> Wählen Sie **Alle Einstellungen anzeigen** aus, wenn der Knoten **Datenbanktools** nicht angezeigt wird.

1. Klicken Sie auf **O/R-Designer**.

2. Legen Sie die **Pluralisierung von Namen** auf **aktiviert**  = **false** fest, um die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] so festzulegen, dass die Klassennamen nicht geändert werden.

3. Legen Sie die **Pluralisierung von Namen** auf **aktiviert** fest  = **true** , um pluralisierungs Regeln auf die Klassennamen von Objekten anzuwenden, die der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] hinzugefügt wurden.

## <a name="see-also"></a>Siehe auch
 [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [den Zugriff auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
