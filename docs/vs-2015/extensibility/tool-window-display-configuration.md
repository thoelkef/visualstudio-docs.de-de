---
title: Konfiguration der Tool Fenster Anzeige | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1af78bd58c42cf1312e36621011802e908c9e919
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186397"
---
# <a name="tool-window-display-configuration"></a>Konfiguration der Toolfensteranzeige
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn ein VSPackage ein Tool Fenster registriert, werden die Standardposition, die Größe, der Andock Stil und andere Sichtbarkeits Informationen in optionalen Werten angegeben. Weitere Informationen zur Tool Fenster Registrierung finden Sie unter [Tool Fenster in der Registrierung](../extensibility/tool-windows-in-the-registry.md) .  
  
## <a name="window-display-information"></a>Fenster Anzeigeinformationen  
 Die grundlegende Anzeige Konfiguration eines Tool Fensters wird in bis zu sechs optionalen Werten gespeichert:  
  
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
  
|Name|Typ|Daten|BESCHREIBUNG|  
|----------|----------|----------|-----------------|  
|Name|REG_SZ|"Kurzname hier eingeben"|Ein Kurzname, der das Tool Fenster beschreibt. Wird nur für Verweise in der Registrierung verwendet.|  
|Float|REG_SZ|"X1, Y1, x2, Y2"|Vier durch Trennzeichen getrennte Werte. X1, Y1 ist die Koordinate der oberen linken Ecke des Tool Fensters. X2, Y2 ist die Koordinate der unteren rechten Ecke. Alle Werte befinden sich in Bildschirm Koordinaten.|  
|Style|REG_SZ|MDI<br /><br /> Hafen<br /><br /> Anknüpfen<br /><br /> Registerkarten<br /><br /> "Alwaysfloat"|Ein Schlüsselwort, das den anfänglichen Anzeige Zustand des Tool Fensters angibt.<br /><br /> "MDI" = angedockt mit dem MDI-Fenster.<br /><br /> "Float" = unverankert.<br /><br /> "Linked" = verknüpft mit einem anderen Fenster (angegeben im Fenster Eintrag).<br /><br /> "Registerkarten" = kombiniert mit einem anderen Tool Fenster.<br /><br /> "Alwaysfloat" = kann nicht angedockt werden.<br /><br /> Weitere Informationen finden Sie im Abschnitt "Kommentare" unten.|  
|Fenster|REG_SZ|*\<GUID>*|Der GUID eines Fensters, in das das Tool Fenster verknüpft werden kann oder im Registerkarten Format angezeigt wird. Die GUID kann zu einem ihrer eigenen Fenster oder zu einem der Fenster in der IDE gehören [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|Ausrichtung|REG_SZ|Linken<br /><br /> Rechten<br /><br /> Oben<br /><br /> Unten|Siehe den Abschnitt "Kommentare" weiter unten.|  
|DontForceCreate|REG_DWORD|0 oder 1|Wenn dieser Eintrag vorhanden ist und der Wert nicht NULL ist, wird das Fenster geladen, aber nicht sofort angezeigt.|  
  
### <a name="comments"></a>Kommentare  
 Der Richtungs Eintrag definiert die Position, an der das Tool Fenster angedockt wird, wenn auf die Titelleiste Doppel geklickt wird. Die Position ist relativ zu dem Fenster, das im Fenster Eintrag angegeben ist. Wenn der Style-Eintrag auf "linked" festgelegt ist, kann der Ausrichtungs Eintrag "Left", "Right", "Top" oder "Bottom" lauten. Wenn der Format Eintrag "Registerkarte" ist, kann der Orientierungs Eintrag "Left" oder "Right" lauten und gibt an, wo die Registerkarte hinzugefügt wird. Wenn der Format Eintrag "float" lautet, schwebt das Tool Fenster zuerst. Beim Doppelklicken auf die Titelleiste werden die Ausrichtung und die Fenster Einträge angewendet, und im Fenster wird der Stil "Registerkarte" verwendet. Wenn der Format Eintrag "alwaysfloat" lautet, kann das Tool Fenster nicht angedockt werden. Wenn der Format Eintrag "MDI" lautet, wird das Tool Fenster mit dem MDI-Bereich verknüpft, und der Fenster Eintrag wird ignoriert.  
  
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
  
## <a name="tool-window-visibility"></a>Sichtbarkeit des Tool Fensters  
 Werte im optionalen Sichtbarkeits Unterschlüssel bestimmen die Sichtbarkeitseinstellungen eines Tool Fensters. Die Namen der Werte werden verwendet, um die GUIDs von Befehlen zu speichern, die die Sichtbarkeit des Fensters erfordern. Wenn der Befehl ausgeführt wird, gewährleistet die IDE, dass das Tool Fenster erstellt und sichtbar gemacht wird.  
  
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
  
|Name|Typ|Daten|BESCHREIBUNG|  
|----------|----------|----------|-----------------|  
|(Standardwert)|REG_SZ|Keine|Lassen Sie leer.|  
|*\<GUID>*|REG_DWORD oder REG_SZ|0 oder eine beschreibende Zeichenfolge.|Optional. Der Name des Eintrags muss die GUID eines Befehls sein, der die Sichtbarkeit erfordert. Der Wert enthält nur eine informative Zeichenfolge. In der Regel ist der Wert `reg_dword` auf 0 festgelegt.|  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegendes zu VSPackages](../misc/vspackage-essentials.md)
