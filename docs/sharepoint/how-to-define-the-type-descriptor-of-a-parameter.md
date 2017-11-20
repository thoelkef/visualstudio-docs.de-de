---
title: 'Vorgehensweise: Definieren des Typdeskriptors eines Parameters | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
ms.assetid: 7494559f-1567-4cbd-bde0-05a2ed288c3a
caps.latest.revision: "32"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 19722a4cffb0e3708939734253b0f2c4a408389e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>Gewusst wie: Definieren des Typdeskriptors für einen Parameter
  Ein Typdeskriptor enthält Eigenschaften, mit denen der Datentyp eines Parameters beschrieben wird. Von einem Typdeskriptor kann ein Feld, eine Entität oder eine Auflistung von Entitäten definiert werden. Weitere Informationen finden Sie unter [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx).  
  
### <a name="to-define-the-type-descriptor-of-a-parameter"></a>So definieren Sie den Typdeskriptor für einen Parameter  
  
1.  In der **BDC-Methodendetails** Fenster, wählen Sie den Typdeskriptor des Parameters.  
  
2.  Wählen Sie in der Menüleiste **Ansicht**, **Fenster "Eigenschaften"**.  
  
3.  In der **Eigenschaften** die Eigenschaften des Typdeskriptors fest.  
  
     In den folgenden Prozeduren wird beschrieben, wie ein Typdeskriptor als Feld, Entität oder Entitätsauflistung definiert wird.  
  
### <a name="to-define-a-field"></a>So definieren Sie ein Feld  
  
1.  In der **Eigenschaften** legen die **Namen** Eigenschaft des Typdeskriptors auf den Namen eines Felds in den Typ, der die Entität darstellt (z. B.: **FirstName**).  
  
2.  In der Liste neben den **TypeName** -Eigenschaft, wählen Sie den entsprechenden Datentyp (z. B. **Int32**).  
  
     Informationen zu anderen optionalen Parametern finden Sie unter [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx).  
  
### <a name="to-define-an-entity"></a>So definieren Sie eine Entität  
  
1.  In der **Eigenschaften** legen die **Namen** Eigenschaft, um einen Namen, der die Entität beschreibt (z. B.: **wenden Sie sich an**).  
  
2.  Legen Sie die **TypeName** Eigenschaft, um den vollqualifizierten Namen des Typs, der die Entität darstellt. Bei diesem Typ kann es sich um eine Klasse im Projekt, um einen im BDC-Objektmodell definierten Typ oder um einen Typ handeln, der in einer Assembly definiert ist, auf die in der Lösung verwiesen wird.  
  
    -   Für eine Klasse in Ihrem Projekt, wählen Sie den Pfeil nach unten neben dem **TypeName** -Eigenschaft, wählen Sie die **aktuelles Projekt** Registerkarte im Dialogfeld, das angezeigt wird, und drücken die Klasse in Ihrem Projekt.  
  
         Der vollqualifizierte Name enthält den Namespace und den Namen der Klasse, gefolgt vom Namen des LOB-Systems. Im folgenden Beispiel wird der Wert der **TypeName** Eigenschaft zu einer Klasse in Ihrem Projekt.  
  
         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`  
  
    -   Bei Verwendung eines Typs, der sich in einer Assembly der Lösung befindet, enthält der vollqualifizierte Name den Namen des Typs, den Namen der Assembly, die Versionsnummer, die Kultur sowie das öffentliche Schlüsseltoken.  
  
         Im folgenden Beispiel wird der Wert der **TypeName** -Eigenschaft auf einen Typ in einer Assembly, die Sie in der Lösung verwiesen.  
  
         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
    -   Bei Verwendung eines im BDC-Objektmodell definierten Typs enthält der vollqualifizierte Name den Namespace und den Namen des Typs.  
  
         Im folgenden Beispiel wird der Wert der **TypeName** Eigenschaft auf einen Typ im BDC-Objektmodell.  
  
         `Microsoft.BusinessData.Runtime.DynamicType`  
  
3.  In der **BDC-Methodendetails** , öffnen Sie die Liste, die für den Typdeskriptor angezeigt wird, und wählen Sie dann **bearbeiten**.  
  
     Die **BDC-Explorer** Fenster wird geöffnet.  
  
4.  In der **BDC-Explorer**, öffnen Sie das Kontextmenü des Typdeskriptors, und wählen Sie dann **Typdeskriptor hinzufügen**.  
  
     Dem Entitätstypdeskriptor wird ein neuer Typdeskriptor als untergeordnetes Element hinzugefügt. Konfigurieren Sie diesen Typdeskriptor als Feld.  
  
5.  Wiederholen Sie Schritt 4, um für jedes Feld der Entität einen untergeordneten Typdeskriptor hinzuzufügen.  
  
### <a name="to-define-a-collection-of-entities"></a>So definieren Sie eine Auflistung von Entitäten  
  
1.  In der **BDC-Methodendetails** Fenster, wählen Sie den Typdeskriptor des Parameters, der werden sollen.  
  
2.  Wählen Sie in der Menüleiste **Ansicht**, **Fenster "Eigenschaften"**.  
  
3.  In der **Eigenschaften** legen die **Namen** Eigenschaft, um einen Namen, der die Entität beschreibt (z. B.: **Kontakte**).  
  
4.  Legen Sie die **"IsCollection"** Eigenschaft **"true"**. Dadurch wird angegeben, dass es sich bei diesem Typdeskriptor um eine Auflistung von Entitäten handelt.  
  
5.  Legen Sie die **TypeName** Eigenschaft, um eine Zeichenfolge, enthält einen Verweis auf, die <xref:System.Collections.Generic.IEnumerable%601> -Schnittstelle, und der vollqualifizierte Name des Typs, der die Entität darstellt. Bei diesem Typ kann es sich um eine Klasse im Projekt, um einen im BDC-Objektmodell definierten Typ oder um einen Typ handeln, der in einer Assembly definiert ist, auf die in der Lösung verwiesen wird.  
  
    -   Für eine Klasse in Ihrem Projekt, wählen Sie den Pfeil nach unten neben dem **TypeName** -Eigenschaft, wählen Sie die **aktuelles Projekt** Registerkarte im Dialogfeld, das angezeigt wird, und drücken die Klasse in Ihrem Projekt.  
  
         Der vollqualifizierte Name enthält den Namespace und den Namen der Klasse, gefolgt vom Namen des LOB-Systems.  
  
         Im folgenden Beispiel wird der Wert der **TypeName** Eigenschaft, um eine Auflistung von Klassen in Ihrem Projekt.  
  
         `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.` ` BdcModel1.Contact, BdcModel1] "  
  
    -   Bei Verwendung eines Typs, der sich in einer Assembly der Lösung befindet, enthält der vollqualifizierte Name den Namen des Typs, den Namen der Assembly, die Versionsnummer, die Kultur sowie das öffentliche Schlüsseltoken.  
  
         Im folgenden Beispiel wird der Wert der **TypeName** Eigenschaft, um eine Auflistung von Typen in einer Assembly, die Sie in der Projektmappe zu verweisen.  
  
         `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, MyAssemblyName, Version = 4.0.0.0, Culture = Neutral, PublicKeyToken = b77a5c561934e089] "  
  
    -   Bei Verwendung eines im BDC-Objektmodell definierten Typs enthält der vollqualifizierte Name lediglich den Namespace und den Namen des Typs.  
  
         Im folgenden Beispiel wird der Wert der **TypeName** Eigenschaft, um eine Auflistung von im BDC-Objektmodell definierten Typen.  
  
         `System.Collections.Generic.IEnumerable`1 ' Microsoft.BusinessData.Runtime.DynamicType [']'  
  
6.  In der **BDC-Methodendetails** , öffnen Sie die Liste, die für den Typdeskriptor angezeigt wird, und wählen Sie dann **bearbeiten**.  
  
     Die **BDC-Explorer** Fenster wird geöffnet.  
  
7.  In der **BDC-Explorer**, öffnen Sie das Kontextmenü des Typdeskriptors, und wählen Sie dann **Typdeskriptor hinzufügen**.  
  
     Dem Auflistungstypdeskriptor wird ein neuer Typdeskriptor als untergeordnetes Element hinzugefügt. Konfigurieren Sie diesen Typdeskriptor als Entität.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)   
 [Vorgehensweise: hinzufügen eine Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Vorgehensweise: Hinzufügen eines Parameters einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Vorgehensweise: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  