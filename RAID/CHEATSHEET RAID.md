## CHEATSHEET RAID

**Redundant Array of Inexpensive Disks** --> Combinar discos para tener redundancia, rendimiento, baja latencia, incremento de ancho de banda y maximizar la habilidad de recuperación en caso de fail.

* Dividir y replicar la información en diferentes discos duros e incrementar la fiabilidad y transferencia.

*Tipos RAID*:

*   RAID 0 = **`DISK STRIPING`** / **VOLUMEN DIVIDIDO** / NO REDUNDANCIA

    * Distribución por bandas.
    
    * Discos con el mismo tamaño o uno mayor que otro.

    * Sin información de PARIDAD. Distribución equitativa.

    * Si falla un disco = Pierde información.

*   RAID 1 = **`DISK MIRRORING`** / **VOLUMEN ESPEJO**

    * Distribución por igual.

    * Tiene REDUNDANCIA.

    * Es una copia a uno o maś discos.

    * Si uno falla, los datos permanecerán intactos.

    * RAID1 sólo puede ser tan grande como el más pequeño de sus discos.

    * Si tenemos 3 discos de 1TB en RAID1, todos tendrán 1TB.

    * Para perder los datos, tienen que fallar todos los discos.

    * Es costoso. 

*   RAID 5 = **`DISK STRIPING WITH PARITY`** 

    * Raid4 + Paridad repartida (Striping con paridad) - Min 3 discos.

    * Tiene redundancia.

    * La capacidad es la suma de todos los discos menos UNO.

    * Sólamente puede sobrevivir a un fallo de disco. Permanecerán los datos gracias a la paridad.

    * Elimina el cuello de botella.

    * Si tengo 3 discos de 1TB a RAID5 cuanta capacidad de almacenamiento tengo?

        * 2TB / La paridad está repartida en los 3 discos y se pierde 1TB.

**SOFTWARE RAID** --> MD Multi Disc.

* Otros RAID

* RAID 2 = RAID0 + RAID1 / Paridad Hamming

* RAID 3 = RAID0 + PARIDAD (Bytes) --> Data striping + un disco de paridad - Min 3 discos (2 ern RAID0 + 1 paridad). If 1 disk fail --> Se recupera con bit de paridad.

* RAID 4 = **``Block Striped (Dedicated Parity Disk)``** --> RAID3 + PARIDAD (Bloques) --> Toda la paridad en un MISMO DISCO --> Genera cuello de botella. Almacenamiento de RAID4 es lo mismo que el más pequeño.

* RAID 6 = **`Striping con Paridad Doble`** --> Lo mismo que el RAID5

* RAID 0 + 1

* RAID 1 + 0

**``Paridad``** --> Es la suma de todos los dispositivos utilizados en una MATRIZ --> Sirve Para recuperarse del fallo del dispositivo. Lee los datos buenos que quedan y los compara con el dato de paridad del almacenamiento conjunto.
Es usada en los niveles 2, 3, 4 y 5.

RAID1 no utiliza paridad.

0. 

1. 

2. 

3. 

4. 

5. 

6. 

7. 

8. 

9. 

10. 

11. 

12. 

13. 

14. 

15. 

16. 

17. 

18. 

19. 

20. 

21. 

22. 

23. 

24. 

25. 

26. 

27. 

28. 

29. 

30. 

31. 

32. 

33. 

34. 

35. 

36. 

37. 

38. 

39. 

40. 

41. 

42. 

43. 

44. 

45. 

46. 

47. 

48. 

49. 

50. 

51. 

52. 

53. 

54. 

55. 

56. 

57. 

58. 

59. 

60. 

61. 

62. 

63. 

64. 

65. 

66. 

67. 

68. 

69. 

70. 

71. 

72. 

73. 

74. 

75. 

76. 

77. 

78. 

79. 

80. 

81. 

82. 

83. 

84. 

85. 

86. 

87. 

88. 

89. 

90. 

91. 

92. 

93. 

94. 

95. 

96. 

97. 

98. 

99. 

100. 

101. 

102. 

103. 

104. 

105. 

106. 

107. 

108. 

109. 

110. 

111. 

112. 

113. 

114. 

115. 

116. 

117. 

118. 

119. 

120. 

121. 

122. 

123. 

124. 

125. 

126. 

127. 

128. 

129. 

130. 

131. 

132. 

133. 

134. 

135. 

136. 

137. 

138. 

139. 
