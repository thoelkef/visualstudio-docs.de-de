---
title: VSIX-Farbcompiler | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c5055da98dd13c5f9f97a28bb420b5ee28d52c10
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948400"
---
# <a name="vsix-color-compiler"></a>VSIX-Farbcompiler
Das Visual Studio-Erweiterung Farbe Compiler-Tool ist eine Konsolenanwendung, die eine XML-Datei, die Farben für vorhandene Visual Studio-Designs darstellt akzeptiert und konvertiert sie eine PKGDEF-Datei, damit diese Farben in Visual Studio verwendet werden können. Da es einfach, die Unterschiede zwischen XML-Dateien handelt, eignet sich dieses Tool zum Verwalten von Farben in der quellcodeverwaltung. Sie können auch Buildumgebungen Hook hinzugefügt werden soll, damit die Ausgabe des Builds eine gültige PKGDEF-Datei ist.  
  
 **Design von XML-schema**  
  
 Eine vollständige Design-XML-Datei sieht folgendermaßen aus:  
  
```xml  
<Themes>  
      <!—one or Theme elements -->  
      <Theme>  
        <!-- one or more Category elements -->  
        <Category>  
          <!-- one or more Color elements -->  
          <Color>  
            <!-- zero or one Background element -->  
            <Background />  
            <!-- zero or one Foreground element -->  
            <Foreground />  
          </Color>  
        </Category>  
      </Theme>  
</Themes>  
```  
  
 **Design**  
  
 Die \<Design >-Element definiert ein vollständiges Design. Ein Design muss mindestens einen enthalten \<Kategorie > Element. Designelemente werden wie folgt definiert:  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**Attribut**|**Definition**|  
|name|[Erforderlich] Der Name des Designs|  
|GUID|[Erforderlich] Das Design der GUID (Formatierung der GUID übereinstimmen muss)|  
  
 Wenn Sie benutzerdefinierte Farben für Visual Studio zu erstellen, müssen diese Farben für die folgenden Themen definiert werden. Wenn keine Farben für ein bestimmtes Design vorhanden ist, versucht Visual Studio, um die fehlenden Farben aus das Design "hell" zu laden.  
  
|||  
|-|-|  
|**Name des Designs**|**Design "GUID"**|  
|Hell|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|Dunkel|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|Blau|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|Hoher Kontrast|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **Kategorie**  
  
 Die \<Kategorie >-Element definiert eine Auflistung von Farben in einem Design. Kategorienamen logische Gruppierungen bereitzustellen und sollten als eng wie möglich definiert werden. Eine Kategorie muss mindestens einen enthalten \<Farbe > Element. Kategorieelemente werden wie folgt definiert:  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**Attribut**|**Definition**|  
|name|[Erforderlich] Der Name der Kategorie|  
|GUID|[Erforderlich] Die Kategorie-GUID (Formatierung der GUID übereinstimmen muss)|  
  
 **Farbe**  
  
 Die \<Farbe >-Element definiert eine Farbe für eine Komponente oder der Zustand der Benutzeroberfläche. Das bevorzugte Benennungsschema für eine Farbe ist [UI-Typ] [Status]. Verwenden Sie nicht das Wort "Color", da sie redundant ist. Eine Farbe sollte eindeutig anzugeben, den Elementtyp und die Situationen, oder "Bundesland", für die die Farbe angewendet werden. Eine Farbe darf nicht leer sein und muss entweder eine oder beide der enthalten eine \<Hintergrund > und \<Vordergrund > Element. Farbelemente sind wie folgt definiert:  
  
```xml  
<Color Name="name">  
        <Background /> <!-- zero or one Background element -->  
        <Foreground /> <!-- zero or one Foreground element -->  
 </Color>  
```  
  
|||  
|-|-|  
|**Attribut**|**Definition**|  
|name|[Erforderlich] Der Name der Farbe|  
  
 **Hintergrund und/oder Vordergrund**  
  
 Die \<Hintergrund > und \<Vordergrund > Elemente zu definieren, einer Farbe den Wert und Typ für den Hintergrund oder Vordergrund eines Benutzeroberflächenelements. Diese Elemente verfügen über keine untergeordneten Elemente.  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**Attribut**|**Definition**|  
|Typ|[Erforderlich] Der Typ der Farbe. Sie können eine der folgenden sein:<br /><br /> *CT_INVALID:* Die Farbe ist ungültig oder nicht festgelegt.<br /><br /> *CT_RAW:* Ein unformatiertes über den ARGB-Wert.<br /><br /> *CT_COLORINDEX:* VERWENDEN SIE NICHT.<br /><br /> *CT_SYSCOLOR:* Eine Windows-System-Farbe von SysColor.<br /><br /> *CT_VSCOLOR:* Eine aus __VSSYSCOLOREX Visual Studio-Farbe.<br /><br /> *CT_AUTOMATIC:* Die Farbe.<br /><br /> *CT_TRACK_FOREGROUND:* VERWENDEN SIE NICHT.<br /><br /> *CT_TRACK_BACKGROUND:* VERWENDEN SIE NICHT.|  
|Source|[Erforderlich] Der Wert der Farbe dargestellt wird in hexadezimal|  
  
 Alle Werte, die von der Enumeration __VSCOLORTYPE unterstützt werden, werden nach dem Schema in das Type-Attribut unterstützt. Allerdings empfiehlt es sich, dass Sie nur CT_RAW und CT_SYSCOLOR verwenden.  
  
 **Alle zusammen**  
  
 Dies ist ein einfaches Beispiel für eine gültige Design-XML-Datei:  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">  
      <Color Name="MyActiveBorder">  
        <Background Type="CT_RAW" Source="FFCCCEDB" />  
      </Color>  
    </Category>  
  </Theme>  
</Themes>  
```  
  
## <a name="how-to-use-the-tool"></a>Gewusst wie: Verwenden Sie das tool  
 **Syntax**  
  
 VsixColorCompiler \<XML-Datei > \<PkgDef-Datei > \<optionale Argumente >  
  
 **Argumente**  
  
||||  
|-|-|-|  
|**SwitchName**|**Notizen**|**Erforderlich oder Optional**|  
|Unbenannte (XML-Datei)|Dies ist der erste unbenannte Parameter und den Pfad der XML-Datei konvertiert wird.|Erforderlich|  
|Unbenannte (PKGDEF-Datei)|Dies ist der zweite unbenannte Parameter und der Ausgabepfad für die generierte PKGDEF-Datei.<br /><br /> Standardeinstellung: \<XML Filename>.pkgdef|Optional|  
|/noLogo|Dieses Flag wird beendet, Produkt und das Copyright-Informationen aus drucken.|Optional|  
|/?|Ausgeben von Hilfeinformationen.|Optional|  
|/help|Ausgeben von Hilfeinformationen.|Optional|  
  
 **Beispiele**  
  
-   VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef  
  
-   VsixColorCompiler D:\xml\colors.xml /noLogo  
  
## <a name="notes"></a>Hinweise  
  
-   Dieses Tool erfordert, dass die neueste Version der VC++-Laufzeit installiert werden.  
  
-   Nur einzelne Dateien werden unterstützt. Das massenkonvertieren über Ordnerpfade wird nicht unterstützt.  
  
## <a name="sample-output"></a>Beispielausgabe:  
 Die PKGDEF-Datei, die vom Tool generierten sollte dieser ähneln dem folgenden Schlüssel:  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```