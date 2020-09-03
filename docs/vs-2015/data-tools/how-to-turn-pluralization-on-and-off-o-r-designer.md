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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665936"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Vorgehensweise: Aktivieren/Deaktivieren der Pluralisierung (O/R-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie Datenbankobjekte mit Namen, die auf s oder IES enden, von **Server-Explorer** / **Datenbank-Explorer** auf die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)ziehen, werden die Namen der generierten Entitäts Klassen standardmäßig von Plural in Singular geändert. Damit soll verdeutlicht werden, dass die instanziierte Entitätsklasse einem einzigen Datensatz zugeordnet ist. Wird dem [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] beispielsweise die Tabelle Customers hinzugefügt, erhält die Entitätsklasse den Namen Customer, da die Klasse die Daten eines einzigen Kunden enthält.

> [!NOTE]
> Pluralisierung ist standardmäßig nur in der englischsprachigen Version von Visual Studio aktiviert.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>So schalten Sie Pluralisierung ein und aus

1. Klicken Sie im Menü **Extras** auf **Optionen**.

2. Erweitern Sie im Dialogfeld **Optionen** den Knoten **Datenbanktools**.

> [!NOTE]
> Wählen Sie **Alle Einstellungen anzeigen** aus, wenn der Knoten **Datenbanktools** nicht angezeigt wird.

1. Klicken Sie auf **O/R-Designer**.

2. Legen Sie die **Pluralisierung von Namen** auf **aktiviert**  =  **false** fest, um den so festzulegen [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , dass er keine Klassennamen ändert.

3. Legen Sie die **Pluralisierung von Namen** auf **aktiviert**  =  **true** fest, um pluralisierungs Regeln auf die Klassennamen von Objekten anzuwenden, die dem hinzugefügt wurden [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

## <a name="see-also"></a>Weitere Informationen
 [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [den Zugriff auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
