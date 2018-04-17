---
title: 'Vorgehensweise: Programmgesteuertes Öffnen von Textdateien als Arbeitsmappen | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cafe64ce693972bd9c254a6bdfc1dcbf70f004c9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Gewusst wie: Programmgesteuertes Öffnen von Textdateien als Arbeitsmappen
  Sie können eine Textdatei als eine Arbeitsmappe öffnen. Sie müssen den Namen der Textdatei übergeben, die Sie öffnen möchten. Sie können verschiedene optionale Parameter, z. B. die Zeilennummer, auf Start und das Spaltenformat der Daten in der Datei angeben.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel benötigen Sie die folgenden Komponenten:  
  
-   Eine durch Trennzeichen getrennte Textdatei mit dem Namen `Test.txt` , die mindestens drei Textzeilen enthält.  
  
-   Die Textdatei `Test.txt` auf Laufwerk "c" gespeichert werden  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Öffnen von Arbeitsmappen](../vsto/how-to-programmatically-open-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Erstellen neuer Arbeitsmappen](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Speichern von Arbeitsmappen](../vsto/how-to-programmatically-save-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Schließen von Arbeitsmappen](../vsto/how-to-programmatically-close-workbooks.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  