---
title: 'Gewusst wie: Ändern des Rückgabetyps einer DataContext-Methode (O / R-Designer) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4999c9fd273b78ff740e53c25bbe5a4b0a3017f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211743"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Gewusst wie: Ändern des Rückgabetyps einer DataContext-Methode (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Der Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode, die basierend auf einer gespeicherten Prozedur oder Funktion erstellt wurde, unterscheidet sich abhängig von dem Ort, an dem die gespeicherte Prozedur oder Funktion im [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] abgelegt wurde. Wenn Sie ein Element direkt auf einer vorhandene Entitätsklasse ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode erstellt, die über den Rückgabetyp dieser Entitätsklasse verfügt (wenn das Schema der Daten, die von der gespeicherten Prozedur oder Funktion zurückgegeben wurden, mit der Form der Entitätsklasse übereinstimmt). Wenn Sie ein Element in einem leeren Bereich von [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode erstellt, die einen automatisch erstellten Typ zurückgibt. Sie können den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode ändern, wenn Sie sie dem Methodenbereich hinzugefügt haben. Um zu überprüfen oder Ändern des Rückgabetyps von einer <xref:System.Data.Linq.DataContext> -Methode, wählen Sie ihn, und klicken Sie auf die **Rückgabetyp** -Eigenschaft in der **Eigenschaften** Fenster.  
  
> [!NOTE]
>  Sie können nicht rückgängig gemacht <xref:System.Data.Linq.DataContext> Methoden, die einen Rückgabetyp auf eine Entitätsklasse festgelegt, um den automatisch generierten Typ mit Zurückgeben der **Eigenschaften** Fenster. Zum Wiederherstellen einer <xref:System.Data.Linq.DataContext>-Methode zur Rückgabe eines automatisch generierten Typs müssen Sie das ursprüngliche Datenbankobjekt erneut auf den O/R-Designer ziehen.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>So ändern Sie den Rückgabetyp einer DataContext-Methode vom automatisch generierten Typ in eine Entitätsklasse  
  
1.  Wählen Sie im Methodenbereich die <xref:System.Data.Linq.DataContext>-Methode aus.  
  
2.  Wählen Sie **Rückgabetyp** in die **Eigenschaften** Fenster, und wählen Sie dann eine verfügbare Entitätsklasse-Klasse der **Rückgabetyp** Liste. Wenn die gewünschte Entitätsklasse nicht in der Liste enthalten ist, hinzufügen oder erstellen sie im der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] um es der Liste hinzuzufügen.  
  
3.  Speichern Sie die DBML-Datei.  
  
### <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>So ändern Sie den Rückgabetyp einer DataContext-Methode von einer Entitätsklasse zurück in einen automatisch generierten Typ  
  
1.  Wählen Sie im Methodenbereich die <xref:System.Data.Linq.DataContext>-Methode aus, und löschen Sie sie.  
  
2.  Ziehen Sie das Datenbankobjekt, das von **Server-Explorer**/**Datenbank-Explorer** auf einen leeren Bereich des O/R-Designers.  
  
3.  Speichern Sie die DBML-Datei.  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Vorgehensweise: Erstellen von DataContext-Methoden, die zu gespeicherten Prozeduren und Funktionen zugeordnet sind (O/R-Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)

