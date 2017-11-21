---
title: Tool Anzeigekonfiguration Fenster | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7ab5cef6fb45d60be8be8d1db6b160079633ed4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="tool-window-display-configuration"></a>Tool-Fenster-Anzeigekonfiguration
Wenn eine VSPackage ein Toolfenster, die Standardposition, Größe, andockstil und andere Informationen zur Sichtbarkeit registriert, wird in optionale Werte angegeben. Weitere Informationen zum Tool Fenster Registrierung, finden Sie unter [Toolfenster in der Registrierung](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>Anzeigeinformationen für Fenster  
 Grundlegende Anzeigekonfiguration ein Toolfenster werden in bis zu sechs optionale Werte gespeichert:  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|Name|Typ|Daten|Beschreibung|  
|----------|----------|----------|-----------------|  
|Name|REG_SZ|"Kurze Name goes here"|Ein kurzer Name, der das Toolfenster beschreibt. Nur für den Verweis in der Registrierung verwendet.|  
|Float|REG_SZ|"X1, Y1, X2, Y2"|Vier durch Trennzeichen getrennte Werte. X1, Y1, ist die Koordinate der oberen linken Ecke des Toolfensters. X2, Y2, ist die Koordinate der unteren rechten Ecke. Alle Werte sind in Bildschirmkoordinaten.|  
|Stil|REG_SZ|"MDI"<br /><br /> "Float"<br /><br /> "Verknüpft"<br /><br /> "Im Registerkartenformat"<br /><br /> "AlwaysFloat"|Ein Schlüsselwort, das Angeben der ursprüngliche Zustand des Toolfensters anzeigen<br /><br /> "MDI" = mit MDI-Fensters angedockt.<br /><br /> "Float" = Gleitkommawert.<br /><br /> "Verknüpft" = verknüpft, die mit einem anderen Fenster (angegeben in der Eintrag im Fenster).<br /><br /> "Im Registerformat" = zusammen mit einem anderen Toolfenster.<br /><br /> "AlwaysFloat" = kann nicht angedockt werden kann.<br /><br /> Weitere Informationen finden Sie unter folgenden Abschnitt "Kommentare".|  
|Fenster|REG_SZ|*\<GUID >*|Die GUID eines Fensters, das Toolfenster verknüpft oder im Registerformat werden kann. Die GUID kann eine eigene Fenster oder ein Fenster in gehören die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE.|  
|Ausrichtung|REG_SZ|"Links"<br /><br /> "Right"<br /><br /> "Top"<br /><br /> "Unten"|Finden Sie im Abschnitt Kommentare.|  
|DontForceCreate|REG_DWORD|0 oder 1|Wenn dieser Eintrag vorhanden ist, und der Wert nicht 0 (null ist), wird das Fenster geladen, aber nicht sofort angezeigt.|  
  
### <a name="comments"></a>Kommentare  
 Der Eintrag Ausrichtung definiert die Position, in dem das Toolfenster dockt an, wenn die Titelleiste doppelgeklickt wird. Die Position ist relativ zum angegebenen Fensters im Fenster Eintrag. Wenn der Style-Eintrag auf "(verknüpft)" festgelegt ist, kann der Eintrag für die Ausrichtung "Links", "Right", "Top" oder "Ende" sein. Wenn der Style-Eintrag ist "Im Registerformat", die Ausrichtung Eintrag "bleiben kann" oder "Mit der rechten Maustaste" und gibt an, wo die Registerkarte hinzugefügt wird. Wenn der Style-Eintrag ist "Float", wird das Toolfenster zuerst verschoben. Wenn auf die Titelleiste doppelgeklickt wird, gelten die Ausrichtung und Fenster-Einträge und das Fenster verwendet die Formatvorlage "Im Registerformat". Wenn der Style-Eintrag "AlwaysFloat" ist, kann nicht im Toolfenster angedockt werden. Wenn der Style-Eintrag "MDI" ist, ist das Toolfenster in den Bereich des MDI-verknüpft, und der Eintrag im Fenster wird ignoriert.  
  
### <a name="example"></a>Beispiel  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>Sichtbarkeit der Tool-Fenster  
 Die Werte im optionalen Sichtbarkeit Unterschlüssel bestimmen eines Toolfensters sichtbarkeitseinstellungen für. Die Namen der Werte werden verwendet, um die GUIDs der Befehle zu speichern, die Sichtbarkeit des Fensters erfordern. Wenn der Befehl ausgeführt wird, garantiert die IDE an, dass das Toolfenster erstellt und sichtbar gemacht wird.  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|Name|Typ|Daten|Beschreibung|  
|----------|----------|----------|-----------------|  
|(Standard)|REG_SZ|Keine|Leer sein.|  
|*\<GUID >*|REG_DWORD oder REG_SZ|0 oder eine beschreibende Zeichenfolge.|Dies ist optional. Der Eintrag Name muss die GUID eines Befehls, die Sichtbarkeit erfordern. Der Wert enthält nur eine informative Zeichenfolge. Der Wert in der Regel ist eine `reg_dword` auf 0 festgelegt.|  
  
### <a name="example"></a>Beispiel  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSPackages](../extensibility/internals/vspackages.md)