---
title: 'Gewusst wie: Programmgesteuertes Öffnen von Textdateien als Arbeitsmappen'
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
ms.openlocfilehash: b7bc7caa5dbceb727394b8543b7659cc43e64a36
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257646"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Gewusst wie: Programmgesteuertes Öffnen von Textdateien als Arbeitsmappen
  Sie können eine Textdatei als eine Arbeitsmappe öffnen. Sie müssen den Namen der Textdatei übergeben, die Sie öffnen möchten. Sie können verschiedene optionale Parameter, wie z. B. die Zeilennummer, zu starten, die Analyse und die Spaltenformat der Daten in der Datei angeben.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]  
  
## <a name="compile-the-code"></a>Kompilieren des Codes  
 In diesem Beispiel muss die folgenden Komponenten:  
  
-   Eine durch Trennzeichen getrennte Textdatei mit dem Namen `Test.txt` , die in den letzten drei Zeilen Text enthält.  
  
-   Die Textdatei `Test.txt` auf Laufwerk c gespeichert werden  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Öffnen von Arbeitsmappen](../vsto/how-to-programmatically-open-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Erstellen neuer Arbeitsmappen](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Speichern von Arbeitsmappen](../vsto/how-to-programmatically-save-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Schließen von Arbeitsmappen](../vsto/how-to-programmatically-close-workbooks.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  