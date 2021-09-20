# GUI_BKCOLOR_TRANSPARENT
#include 'GroupEx.au3' #include &lt;GuiComboBox.au3>   Global $iGUIColor = 0xFFF9E5 Global $iBGColor = 0xE0F9FF, $iBorderColor = 0x00008B, $iTextColor = 0xC60707  Enum $lbName, $inName, $lbStatus, $inStatus, $lbOrt, $inOrt, $cbNormal, $lbNormal, $combo, $radio1, $radio2, $iCount Global $aID[$iCount] Global $radio3, $radio4  Global $hGui = GUICreate('Example GroupEx', 900, 700) GUISetBkColor($iGUIColor)  ; create group with title style italic, default align left Global $tGroup1 = _GuiCtrlGroup_Create($hGui, 'Device Information', 10, 55, 880, 155, $iBorderColor, $iTextColor, $iBGColor, $_GROUPTEXT_ITALIC)  $aID[$lbName] = GUICtrlCreateLabel('Title', 25, 83, 70) _BKTrans(-1) $aID[$inName] = GUICtrlCreateInput('', 100, 80, 200, 21)  $aID[$lbStatus] = GUICtrlCreateLabel('State', 310, 83, 40) _BKTrans(-1) $aID[$inStatus] = GUICtrlCreateInput('', 355, 80, 115, 21)  $aID[$lbOrt] = GUICtrlCreateLabel('Location', 485, 83, 50) _BKTrans(-1) $aID[$inOrt] = GUICtrlCreateInput('', 535, 80, 100, 21)  $aID[$cbNormal] = GUICtrlCreateCheckbox(' ', 655, 83, 13, 13) $aID[$lbNormal] = GUICtrlCreateLabel('  Current Sample', 670, 83) _BKTrans(-1)  $aID[$combo] = _GUICtrlComboBox_Create($hGui, '', 100, 110, 200, 30)  $aID[$radio1] = GUICtrlCreateRadio(' ', 320, 113, 13, 13) GUICtrlSetState(-1, $GUI_CHECKED)  $aID[$radio2] = GUICtrlCreateRadio(' ', 340, 113, 13, 13) _GuiCtrlGroup_Close()  $radio3 = GUICtrlCreateRadio(' ', 100, 350, 13, 13) GUICtrlSetState(-1, $GUI_CHECKED) $radio4 = GUICtrlCreateRadio(' ', 120, 350, 13, 13)  GUISetState()   _Msg('Move group downward by 100px with all internal controls ($aID)') _GuiCtrlGroup_Set($tGroup1, '*,100', $_GROUP_MOVE_REL, $aID)  _Msg('Group title - set default style') _GuiCtrlGroup_Set($tGroup1, '', $_GROUPTEXT_DEFAULT)  _Msg('Group title - set background color - feasible, but not so nice') _GuiCtrlGroup_Set($tGroup1, 0xAAAAFF, $_GROUPTEXT_BACK)  _Msg('Group title - set background again transparency') _GuiCtrlGroup_Set($tGroup1, '', $_GROUPTEXT_TRANS)  _Msg('Group title - set text color') _GuiCtrlGroup_Set($tGroup1, 0x000080, $_GROUPTEXT_FORE)  _Msg('Group border - top and right - change color') _GuiCtrlGroup_Set($tGroup1, 0xFF1234, BitOR($_GROUPBORDER_TOP,$_GROUPBORDER_RIGHT))  _Msg('Group title - centered') _GuiCtrlGroup_Set($tGroup1, '', $_GROUPTEXT_CENTER)  _Msg('Group title - right') _GuiCtrlGroup_Set($tGroup1, '', $_GROUPTEXT_RIGHT)  ConsoleWrite('CREATION BG: ' &amp; $tGroup1.BGPrev &amp; ', hex: 0x' &amp; Hex($tGroup1.BGPrev,6) &amp; @CRLF)  _Msg('Group area - change color') _GuiCtrlGroup_Set($tGroup1, 0xAAFFAA, $_GROUPBACKGROUND)  _Msg('Group DISABLE (with all controls inside), border color and title BGColor stay unchanged') ; _GuiCtrlGroup_SetState(ByRef $_structGroup, $_iState, $_aCtrlInside=Null, $_iTxtColor=Null, $_iBGColor=Null) ; Here, the current color of title text and group area is stored before the disable color is set. ; With Null for colors, the defaults will used. _GuiCtrlGroup_SetState($tGroup1, $GUI_DISABLE, $aID)  _Msg('Group ENABLE (with all controls inside)') _GuiCtrlGroup_SetState($tGroup1, $GUI_ENABLE, $aID) ; without color parameter, the previous colors will used ;~ _GuiCtrlGroup_SetState($tGroup1, $GUI_ENABLE, $aID, Null, 0xAAAAFF) ; you can change the title and group area (BG) color (to omit one, use Null)  _Msg('Group HIDE (with all controls inside)') _GuiCtrlGroup_SetState($tGroup1, $GUI_HIDE, $aID)  _Msg('Group SHOW (with all controls inside)') _GuiCtrlGroup_SetState($tGroup1, $GUI_SHOW, $aID)    Do Until GUIGetMsg() = -3    Func _BKTrans($_iID)     GUICtrlSetBkColor($_iID, $GUI_BKCOLOR_TRANSPARENT) EndFunc  Func _Msg($_sMsg)     MsgBox(262208, 'Action', $_sMsg, 5) EndFunc
