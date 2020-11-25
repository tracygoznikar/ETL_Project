{
 "cells": [
  {
   "attachments": {
    "download.jfif": {
     "image/jpeg": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxASEBASERAWFRUVFhAQFhUYEx4WFhUYGBgXFxcWFRoYHSghGRonGxcYIjEhJSkrMC4uGB8zODMuNygtLisBCgoKDg0OGxAQGCslICUvKy0tLS0vLy0tLS0tLTctLS0tLS0yLS0tLS0tLS0vLS0tLS0tLS0tLS0tLS0tLS0tLf/AABEIAKMBNgMBEQACEQEDEQH/xAAcAAEAAgMBAQEAAAAAAAAAAAAABAUBAwYHAgj/xABKEAABAwEDBwcICQMBBwUAAAABAAIDEQQSIQUGMUFRUqETFBUWYXGRIjRTgZKx0dIHMjNCc7LC4fAjs8FyYmOCg6Li8TVDVHSE/8QAGgEBAAMBAQEAAAAAAAAAAAAAAAECBAMFBv/EADYRAAIBAgMECAUEAwEBAQAAAAABAgMRBBJRFCExQQUTM2FxgZGxFSIy0eFCocHwI3KCQ/E0/9oADAMBAAIRAxEAPwD2tZSwQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAEAQBAfL3hoq4gDaTT3qLhK5r51H6RntD4qMy1JyvQc6j9Iz2h8UzLUZXoOdR+kZ7Q+KZlqMr0HOo/SM9ofFMy1GV6DnUfpGe0PimZajK9BzqP0jPaHxTMtRleg51H6RntD4pmWoyvQc6j9Iz2h8UzLUZXoOdR+kZ7Q+KZlqMr0HOo/SM9ofFMy1GV6DnUfpGe0PimZajK9BzqP0jPaHxTMtRleg51H6RntD4pmWoyvQc6j9Iz2h8UzLUZXoOdR+kZ7Q+KZlqMr0HOo/SM9ofFMy1GV6DnUfpGe0PimZajK9BzqP0jPaHxTMtRleg51H6RntD4pmWoyvQc6j9Iz2h8UzLUZXobQQRUYjSpIMqQEAQBAEAQBAYc4DEmnegMMeDoIPcaoD6QBAEAQBAEAQBAcz9IXmg/Fj9zljxvZeaNWE7TyPIco5YZC+65vdhXZ8VloYJ1o3iaquJVN2ZF6zRbOBXb4XM5bdAdZotnAp8LmNugOs0WzgU+FzG3QHWaLZwKfC5jboDrNFs4FPhcxt0B1mi2cCnwuY26A6zRbOBT4XMbdAdZotnAp8LmNugOs0WzgU+FzG3QHWaLZwKfC5jboDrNFs4FPhcxt0B1mi2cCnwuY26A6zRbOBT4XMbdAdZotnAp8LmNugOs0WzgU+FzG3QHWaLZwKfC5jboDrNFs4FPhcxt0B1mi2cCnwuY26BY5Lt7ZgSBgOxZcRhupdmaKNbrFdHt2QfNLL+DB+Rq9Sh2UfBex5lbtJeLJ67HMIAgCAIAgKq3ZQeXGOEgXcHyEVDTutGt3ALrCnfeyrZAjsUbqOe0vdrMhvHjh4YLst3Ag+ILFGWMcYw111pJaLjgaVP1aGtdSAl2TKEkV0TEujNBfNL8ZOqSmBGq8FylT5olMvFxLBAEAQBAEAQHM/SD5oPxY/c5ZMb2XmjVhO08jwbO77Vvcf0rv0Z2bKY760US9IxBAEAQBAEAQBAEAQBAEAQBAEAQBAEB12Z/wBm7vK8LpPtEergfoPf8g+aWX8GD8jVpodlHwXsZK3aS8WT12OYQBAEAQEXKdpMcMjxpAo3/UTdbxIUxV3YhlVZoLgDb1RTZiXfedXXU4rUVNViynBK6Vkcgc+JxZIzQ9hBp5TTQgHUaUIxBIQG602lkbbz3UFaDWXHdaBi53YASgI7TLIcW8nHra4B0jxsI0MafWSD90oC1yHKTGWONTE4xV1kChYT/wAJHgs9RWZZFiqEhAEAQBAEBzP0g+aD8WP3OWTG9l5o1YTtPI8Gzu+1b3H9K79GdmymO+tFEvSMQQBAEAQBAEAQBAEAQBAEAQBAEAQBAddmf9m7vK8LpPtEergfoPf8g+aWX8GD8jVpodlHwXsZK3aS8WT12OYQBAEAQFbl/wCxrqD4XHuD2q9P6iGRI4yNL3O7w39LQtBUrst5HbPccAGyNPkzglskQ0m4WULqkAXSQ01xrShAxkixTMkkdMWSVoY5fK5QNdpic11Q0CgxaQHaS0HE1jwRaf1OxZyMJ0OLe6mPtAqxU3ZDHlWg1r5cba7SGNro71xq8USi2XIsEAQBAEAQHM/SD5oPxY/c5ZMb2XmjVhO08jwbO77Vvcf0rv0Z2bKY760US9IxBAEAQBAEAQBAfbYnFrnBri1tA5waS1tcBeOgV7UAjhe4Oc1ji1lLzg0lrK6LxGDfWgPlrSSAASSQAAKkk6ABrKAusn5o5SnvclYZjdJDrzOSAIrUVlugkUxGpLixjJuaVvtAvQ2Zzm33RXrzALzfrDF1TTaK7NKi5Ni/s30W24uhE0kEIlcYm1e5zi/k3yBoaG0OEbvvYcEzCxyU2Tni0uswoXiZ1mGoOcH8mDXUCfepIPRbBmbk2J9rhtUdocbJEJZrU5/JQF5YHhkDWm84EXqE1+qa6Qq3ZayPLiRqBA1A6R39qsVCA67M/wCzd3leF0n2iPVwP0Hv+QfNLL+DB+Rq00Oyj4L2MlbtJeLJ67HMIAgCAIDVaoBIx7HaHAtPr1onZ3IKKyOdVzJCb7KNcNXY9u0O0rUnfeiptkdVrqHU4esVB4qJcGWh9SPoPFKg4UrXVTTVWKmm1y3QHAmtQGtH3ydDfWgLbJdlMcQa41cavedrnYn1avUs0pXdyyJaqSEAQBAEAQHM/SD5oPxY/c5ZMb2XmjVhO08jwbO77Vvcf0rv0Z2bKY760US9IxFpbM3rXE6zsfA8PtDQ+Jt03nAkilNIdtB0Ag60uDfkXN2WXKENhlY6N7pAyQEUcxgF+Q6xW4CQdGhRcmx0uWMxbOxmVZo5nUsl1ohoKte4B9HuJN5oa4CopU3jhSii5LRV5x5rxWfJ+TbRE98ktqDXuBAAF9jXMjYBrBJFSca+Ep7yGjoM5cxLFDYmuikpPZ3WTnjrznNuS+S6QMxu0Pl+Tqa7sUXJsWGTM1s33We02pj5LRHZvtKGSoutDnGlG1FMdlRTsS7Fkee53Wyxy2m9YYOSgDGMDSKFzhUue7E4mtNOhoUohnRRyPs2bTnxyOJtlodA5gxa2l+9UGoq5sLRhQi9pTmOR2EeT7NbLLZ7FkzKzYuRgcZImsDuUqLkkkx8k/eIxH3j2Ur4lvA8lyXGYrfZ2uIJitcLSQatNyZoJadYwwKuUPXs+bJy9otMEbrZapTcpC2QwWWzVY0i+8lrHk4uobxo7RgqIuzmc0LblCwZSsFhmtLDD/U/pRlrmAObJgXXA69fA06xSuBpLtYhbj56QnbnOxkksrmMtha2N8jntbyjCwFrSaN8l+oYApyHM0Zz5ichJbp7RboLP/Umms8RN6SWrnPaKNILDo0B2nUpTIaIsGVbTNkO2NcHvu2hj5J3SDGvN2tjdeN57qDVoAGrBOY5HEKSAgOuzP8As3d5XhdJ9oj1cD9B7/kHzSy/gwfkatNDso+C9jJW7SXiyeuxzCAIAgCAICHb8ntloalr2/Ve3SOw7R2FWjNxIaK02S0MF3k2SNGALHXMP9LsB6iuvWRfEhXR82ezWm61rYQ2ga28+QHQKVoytVLqRFmT8n5KbGQ5xvvAug0o1g2Rt+6OK5Sm2SkWKoSEAQBAEAQBAcz9IPmg/Fj9zlkxvZeaNWE7TyPBs7vtW9x/Su/RnZspjvrRRL0jEe5/R7NZ7Tk+x2u0OAfkx0zTITi1jYi0BxON0sc1x7WqrLIssl5TsFpjfl1rCx8MNpheDSvklrhfoDV1GinZJo0KO4m/M4z6LLe+Wz5avtZI5zecOEovxOc5sv2gqKgltCMKjBSyEWPS9gtMeQ5bXaIIOSAtJia26xpYwgNAApGA8NIbruU00QncU+b2fDbXbLRBbBBFZrWy0Rl3Jtjdo/pctLrIjBZWulw7EaITK7M7KVngsOWbNPaGC+wsjo77Z117ax0PlNNGn1jToUshHCqSDq8mZ1RDJc2TrTZzI2sksD2uumOQ4tLu55JrjgSKFRbeSmbsqZ7gWd1kydZm2SBwaJHAkzy4UN94PeKmpI1hLC5yEUha5rm4Fpa4HYQajiFJB1Ocn0hZRtoDXyiJmtkN6MO7Xm8Se6oHYoSJbOdydbpIJmTxmkjHX2kiuOip26VJBm15SmlnNokkLpi5shkwa682lHC6AARQUoBoQDKUsj38pNI6SWQco9zjedQ/UqSa/VxpoALUBHvml2ppW9SuFdFaaK01oD5QBAddmf8AZu7yvC6T7RHq4H6D3/IPmll/Bg/I1aaHZR8F7GSt2kvFk9djmEAQBAEAQBAEAQBAEAQBAEAQBAEBzP0g+aD8WP3OWTG9l5o1YTtPI8Gzu+1b3H9K79GdmymO+tFEvSMRMsmVLRFHNFHM9kcwDZWB1GvGIo4dxIO0YFAaYrXI1j42yODH3S9gcQ113ReGulSgFntcjA8Mkc0PFx4BIDhscNf7naUBpQBAEAQBAEAQBAEBvskYJJcPIYL7u0aA31kgesnUgNcshc5znGpJJPeUBKs+S5n4hlBtdh+6Amszdfre0dwJ+CEXPvq4fSj2P+5BcuMiWfkGlrjeqa1AXnYzBzrSzRa8zbhsTGmrNM9mzVy9ZZYYImTN5RscbCw+S6rWgG7e+to1VVoUpU4JPkkcpzUptrU6FSQEAQBAEAQBAEAQBAEAQBAEAQBAEBzP0g+aD8WP3OWTG9l5o1YTtPI8Gzu+1b3H9K79GdmymO+tFEvSMQQBAEAQBAEAQBAEAQBAfcDQXNB0EiqAtLfCBEQ1oHlB5oNNAQPUKk+soQmQcnEcrGSK41p6kJOuinadaEG2vapBinaoBm8BrUgjz2oNFQcRiKbdWOpAfoKxOJijJNSWMNdtQMVgZ2OBzgz+dG+azMa7lGzvjv0pSMUoG0qbxNW1pgMaE0B7RpX3lHLkdtkS0vls8Ukl285tTdIIPbgSB3AkDRU0qeUlZl0TlBIQBAEAQBAEAQBAEAQBAEAQHM/SD5oPxY/c5ZMb2XmjVhO08jwbO77Vvcf0rv0Z2bKY760US9IxBAEAQBAEAQBAEAQBAEAQHSZmOjktDYpiTXFmODiMbrtejH1UVZNpbi0Em95eZRzTEdqjniFYi53KM3LzXCrdrSTo1V2aMmKqNUJNcVb3NmFpJ4iKfB3v6MPyKCTybtBDaUrQnECu1YafSs4tRqRv3rn9/I2z6KhNZ6cnG++0l/WvM32jNi2RNvyQOa3eI0d+z1r0HjYxjmnCSXh9mYFgZSllhOLfj90R2ZPlcQ1rCSTQAYknYANKoukaDdk3fwZaXRteKu0kvFEm25q2yJodLCWNP3jiPXTR61atjFSV5Qlby+5WjgXVllU4/v8AY0w5GaMXm92aAvMrdK1JK0Fbv4s9Wj0RTi71Hm7uCPV5MtNis8MceMnJRjsZ5I07T2eK9CkrwV9EeVVX+SXi/c53NXMFrnutNtdyxc8yMafqvqbxklFMSST5OjbWtB3lV3WRmyWe89EAXEuZQBAEAQBAEAQBAEAQBAEAQBAcTn5bZXHmzYSWjk5b4BONDhQCmtefjJyfyKPfc3YWEV87Z59bc3TK68+J52f03Yfyi40q9WkrRT9DtUpU5u8miP1Rb6F/sOXTbcRo/T8FNmo9w6ot9C/2HJtuI0fp+Bs1HuHVFvoX+w5NtxGj9PwNmo9w6ot9C/2HJtuI0fp+Bs1HuHVFvoX+w5NtxGj9PwNmo9w6ot9C/wBhybbiNH6fgbNR7h1Rb6F/sOTbcRo/T8DZqPcOqLfQv9hybbiNH6fgbNR7h1Rb6F/sOTbcRo/T8DZqPcOqLfQv9hybbiNH6fgbNR7h1Rb6F/sOTbcRo/T8DZqPcOqLfQv9hybbiNH6fgbNR7h1Rb6F/sOTbcRo/T8DZqPcfUeagaQ5sUgIIcCGOqCMQQm24jR+n4Gz0e4vrdypskoLHh4AxLSK+UMQVsoYmMo/5FbW/DecqlGWb/Hx5W47t4+jfKJdbo2TUNGvLScPLGDa6q4mnaQu0MBRhUVSH48jlU6QqzpunP8APgddm7nbJap7TDPFGIgyR1AH32AENLJg4XSTU6CMRSh1anG6szJGqk7riVGYcwFqJfFIDyb7l5hHlVbhU/eLa8V5uDwM6NRylbuPUxuPhWpqMb95PyBnVPamW1lsjiuNjcf6bXi5U3RE8yfWea4YDEHDZ6UoZk4vmeXCtlkmuR5laMqyvF1ou1wwxd4rBT6NoUVmqO9tdyPRq9J16zyU1a+m9+v4PVM3sgukbFJKC1gDXXdb8Bp/2feuzlmSaM0vkbjz4HYqDmZQBAEAQBAEAQBAEAQBAEAQBAEAqgFUAqgFUAqgFUAqgFUAqgFUAqgFUAqgFUAqgFUBTZ5PAsNoJNAAwk/8bVxr05VKbjHiaMLUjTrRlLgeYQtaavF3UAdJcDQ1BAwoQNexeRGvVoStBtdz+34Pelh6WIgusSl3r+OZLnt8z23XSOI7XOOOomrsSNVarQula609PyZn0Ph73V/UrbLZBG6806iP5Q17fUrfFa+kfR/ch9D0Hzl6r7FhPbJX0vyOdQ1F57nAHbRziKqkulMQ+Fl4L73LR6Iwy4pvxf2sQOTiiaTQNA1rM5VsRK13JmxRo4eN7KKPZcmtpBCNkcY/6QvdgnGKTPmKklKbkubZJVigQBAEAQBAEAQBAEAQBAEBSdZodyTwb8yrmA6zQ7kng35kzAdZodyTwb8yZgOs0O5J4N+ZMwHWaHck8G/MmYDrNDuSeDfmTMB1mh3JPBvzJmA6zQ7kng35kzAdZodyTwb8yZgOs0O5J4N+ZMwHWaHck8G/MmYDrNDuSeDfmTMB1mh3JPBvzJmA6zQ7kng35kzAdZodyTwb8yZgOs0O5J4N+ZMwHWaHck8G/MmYDrNDuSeDfmTMB1mh3JPBvzJmBU515YinsU8LQ8F7WtBIFB5TTjR3YqVK3VRzrkdsPRVWooPnf2PKeZzRnCve0q6xmFrq07f9L+Tq8Fi6DvTvbWL/AINrLbMNJPrb+ynY8JPekvJ/kjbcZDi35r8G02+TaPBPhuH0/dj4pidV6Gl9smOgn1N+ATZMHT3tLzf3ZG142pwb8l9kahk+aQ+VXvcaqs8fh6MbU9/cuHqWh0dia8r1N3e3d+n/AMPZrDnHE2KJpbISGMaTRuJDQK/WSM7pMz1I5ZtLk2b+s0O5J4N+ZTmKDrNDuSeDfmTMB1mh3JPBvzJmA6zQ7kng35kzAdZodyTwb8yZgOs0O5J4N+ZMwHWaHck8G/MmYDrNDuSeDfmTMB1mh3JPBvzJmA6zQ7kng35kzAdZodyTwb8yZgOs0O5J4N+ZMwHWaHck8G/MmYHnvSzt0cV5m2y0R6Oxx1Y6WdujipWMk+SIeDiubHSzt0cUeNlyQ2OOrHSzt0cUWMk+SDwcdWOlnbo4qNtloNjjqOlnbo4qVjJcbIbHHVjpZ26OKjbZaInY46sdLO3RxUvGSXJELBxfNjpZ26OKLGSb4IPBxXNjpZ26OKjbZaDY46sdLO3RxU7ZK17IbHG/FjpZ26OKjbJaIbHHVjpZ26OKl4yV+CCwcdWOlnbo4osZLRB4OOrHSzt0cVG2y0ROxx1Y6WdujipeMloiFg46sdLO3RxUbbLRE7HHVjpZ26OKl4yWiI2OOrHSzt0cUWMlohscdWR8oZXdyT/IGrbtCtCr18uqasnuCp7P/lW9og2bKkTgcbpJB8quFBSgOgD4LnX6PxCd7ZvD+eZvw/SGGcVFfLblwX2JLXMOgtPgVilRnH6ov0N0a1OX0yT8z6uN2BVyvQvdHy6RjdLmj1gK8aFSX0xfoc516cfqkl5kO1ZXjaDd8o9mj1krbR6MrTfzfKv39DFW6VoQXy/M/wBvX7XLeLKzrrfJGgbdittTTypcDA8MpfM3xPrpZ26OKrtstETscdWOlnbo4qdsla9kRscb8WOlnbo4qNtloNjjqx0s7dHFS8ZJckFg46sdLO3RxRYyT5IPBx1Y6Wdujio22WiJ2OOrHSzt0cVO2SteyI2OOrHSzt0cUWMlog8HHVjpZ26OKjbJaIbHHVjpZ26OKnbJW4IbHHVjpZ26OKjbZaInY46sdLO3RxU7ZK10kRscdWOlnbo4qNtloidjjqyuWNK5rbMqW+SIS5swoSuSZUt8kQtTChK5LZlS2EEWpD0MKCTKngiOLMKCTKl6EIItQ9DCgkyp5EczCgkyplxIXAwoJMqZcSFwCR4oS4GCK4FQm1vRLV9zIMmS2H6pLezSF6dLpKpFfMr/ALP++RhqYGDfyuxr6NcNDgeC0rpWnzi/2/BwfR8+TR9cxd/s/wA9Sv8AFKVr2f7fcrsFTu/vkfPRpOlwHqquculYcov++pddHy5yRuhyaxuJ8o9ujwWSr0hVqRst3h9zRTwdODu95MXnrcbDKl8QuASOhDMKCTKl71cjmYUJ2JMqWggi0IZhQSZU8URwMKE7EmVLXNELQwoTsSZVrX4EXtxNsFmc/QMNp0KUm+HAeJPZk5lMSSfBXVNEXPro+Pt8VbIhc5dnKyzOZG6mL6VdQAA9g2L2OooUaSlKF+HK/ueT1larUcYy17jZbbHaYWhz3ggkNwcTjifvNGxRSWFrPKoftb2LVNopLM5fz7l1kuBkkLHmtSDXHWCQfcvNxFCMKjijfQqOdNSZK6Pj7fFcsiOtx0fH2+Kjq4i46Pj7fFS4Ji58vsUYFTXx09gRU1fcLlTI/E0GHiuLSvuJufN8qWt1iExfVbE3F8q0lvsQmW2T7KLtXAEnHEaBqXSEUt4bJXN2bjfAK2VaC45uzcb4BMq0FyDll7YoXOaxt6rWirQdJ+FV3w1GNSpaSOGIqOnTuilsbLVMHOY5tAbuIa3GgOFG9oW+pDC0Wk4GKnLEVVdSMWS0ysnbHJQ+WGOBDTpwwNO0JUw1CdJzhHldCFerGqozfOx1PN2bjfALycq0PTHN2bjfAJlWhNz5fZWEEXQO0ChChxVrC5S2hjmOLT/5G1cXGxNzXfKlIhsX1WxNxfKs1uIvvF9VsTcsbCyN48puPeceOld1CLVyL8iXzGPd4n4pkQuOYx7vE/FR1cRccxj3eJ+KnIhccxj3eJ+Kjq4i7OZnvyWl0UbrvlOaMaDyQa1IqdRXrwoUadFTnG+5d/ueXOrVnVcIytvFvydaIW33SAiobg91ansIVqM8PVllUF6IirTrU1mc/wB2WmQY2yQ1eKkOc0mp7CPesOMoQhU+VWRswtSU6e9llzGPd4n4rLkRpuR58na2H1H/AAVSVPQm5Aewg0IoVyasSbulXfwfuvQVNNXOdx0q7+D91PVoXBys7+D906pEOVjm7JaXRva9ukV066gg18V7VWmqkXFniUqjhJSRLyjlZ8zWtc0AA3sDXGlNnaVxoYVUpN3udq+J61JWsTMkZQcyINGou1bcf8rLjKadS/cbMHL/AB27yb0q7+D91l6tGq46Vd/B+6dWhc3Wa2SvNGjvNMAqyjGPEJk6xMDzaRJRzmWW0StpoaQAAe/yvcojleZaRbKVG1a2qOeWRK7OrCN3CCmPEMy04hQuO8knvyk8AGgoa0w2adf8qtcFGXAo3Y+OlnbB4fur9UhcdLO2Dw/dOqQuV+W7e6RjWneveAI/ytmChabfcYsbL5Eu8hZPypJCHBgaQ4g46jowp/MFqr4aNVptmSjiJUk0kaDaHGTlHfWLr+GjTXBdFTShkWljm5tzzvW50nS7tg8P3Xi9Wj3LjpZ2weH7p1SFx0s/YPD906tC5i3TuNA8AHA6MRXUs1Rx4IsiGuSdmHwCNW3BBStAwqkljm/ZeWtDIr128JMdhaxzmnxA4rRh1mnl8fY5VZZFmPua0StYHhwc00xAGFduCvDLLgXe4jdKP28AunVoi46Uft4BOrQuOlH7eATq0LnPxWpzZeUGm8XeNa+9ezKmpU8nceJGplqZ+835QyrJM0NcAADe7zQjYNq5UMLGk817nWviXVVrWJGRba5jXNG2ugbKf4XDGwTkn3GjAy+VrvLHpR+3gFi6tG646Uft4BOrQuZ5852mh72grlUyx3NEreTc2LLHJa4mPYHNPK1BFQaRvI4gFMLJurFSe7f7M513aDa/u80ZRhjbZLA8NaHPFqvHQXXZaCu2gwUSlLqab5u9/UR7SS8PYqJXC67EaD7lFKU3ON3zRNSyg/ApwV9KeCZQG+C1XARdrrrWn+FkxGFdWSanby/JqoYnqotZblm0g7F4ead7XZ626xvsbAZYwRUF7ARtBcKhRGpJzW/mvcSVosnZaeY7TaGRm61ssga1uAAvHAAK9Z2qy7mVpu8Ebs3DXnpP/wAO1foSh+v/AFkRW/T/ALIplx5HXmFUkK3IjmFUkmZKaHz2eN2LHTQgtOg1e0Hgu1JtTitWvc5z+mT7n7FhbLFEIbe4MAMdqEbDutvPF0dmAWiUmoVHpKy8LnOL+aK1RRXQs3WztxO1lcrLbOHGgFLpIK9rBUpRjmlK90jysXVU3lS4XI63GMwgLayzB4qBShovn68J0ZqLle57dGqqscyRc5s2Vklss7HtDmucQQdBF0n/AAqYacpVYpvd+C1b5abaPu1QsbZLLI1oD3SWmrtZDS274VUym+qg9W/ciN88l4FZI8uJJNTtWV8d52PlQSFZkIKE7O4YRqzCLrM3z6D/AJ39p674Tt4+fszliOzfl7lNHI4NoHGlNFcPBcFdczrxLTKMDBY7A4NAc7nd5wABddkAbeOugwWmUn1UN/HN77jjH65d1vYqTRcM8tWdtxEtNtDTQNB0H61P8L0MNhZVoZs9t/8AeZjr4nq55cpXL2jyTKAmZNI8r1f5XldJtrLZ6/wejgP1eROcRQ6F5TnNx4s9Ddc6/K1iha7KQETBycdiu0YBdLuTvFuGBNTXvWys7Orbko28zNTbah33OXACwZr/AFbzXbQucz/PoP8Am/23rRhf/wBEfP2Zxr9k/L3K3LPmGTe/KH91i6f+FPz9yi7SfkUSpyLczqMq5Ng5pynJNDxZMlvvAXTee+Vr3GmkkNAJOwLe6s4UrxfKJlVKEp71zZyfIN7fE/FcdsrZb5v2RfZqV+HudTLkuBhluxN/9NinxF6kjjFV4rWjsTiNq6TrTd03+i/mUjTgrNL9RzSxcjVzJ+TZDysGP/uR/mCpFLOvFe5aTeVk3OJ557ah/vpfzFdMSlnl4srRfyrwRHhtD2XrjiL7TG6mtrtLT2GgXCMmr20sdZJO1z4UPkSgqkhWfIhBVJJuRfOrN+NB+dq7U+1j4x/g5z+iXgy3t32GUv8A7g/NIu0+zqf7fyco/XD/AFObWXkaOZf5NyHZpobO6SIFzpLYHOBLXEMhLmglpBNCAvSw1WcacEnzl7NmGvTjKcm1p7nJGyswwPtH4qIYys43cv2RMsNST4fuyzyFkmCR0wey9dgtMg8p2DmsJacDtRYus83zfpb4LkQ8NTVt3NalhnHZY4pmsjY1jRFAaNFBUsBJw1kmtVwxTbrJvRHegkqbS7zZmb5/Zv8AU78jlzwnbx/vJlsR2TPm2+YWD/VbPzMUS7Cn/wBe4j2svIqFylxZ1XAKpIU8iOYUEhWfIhFtmo4i2Qkf73+29dsJ28fP2ZyxHZvy9ymBwHcuC4LwOvNlxlZx5jk3/wDb/dC0VF/hp/8AXucYdpPy9jnJTUmqgknWGzMdZbe5zGksZZy0kAlpMzGktOqoJGC70qkoQm4u3D3OVSEZSimtfYxnRk2GK0lkbLrbkDqBx0uja46TtJWmriasajSemhwhQpuN2jVkSwxvM99tbtmtcgqTg5sbi06dRxVYYqrKTTfJ6Fnh6aSduaJ+dFnZHbJGRsaxoZZ6NaAAKwxk4DtJK4Ytt1Hfu9jrh1aC8ysfoPrWRvcaDvMt/Xyz3ZO98a2YjjW/4/gzUf8Az/6OSXmm0//Z"
    }
   },
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "![download.jfif](attachment:download.jfif)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# ETL Technical Report"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Purpose"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "<blockquote>The purpose of this project is to introduce students to extracting, transforming, and loading data into a database for retrieval. The requirements of this ETL Project included the following:\n",
    "<br>\n",
    "<ul>\n",
    "    <li> Project must use 2 or more sources of data. Recommended sites are: <a href=\"https://data.world/\">Data World</a> or <a href=\"https://www.kaggle.com/\">Kaggle</a> (APIs can be used as well)</li><br>\n",
    "    <li> A technical report must be submitted which details sources of data, type of files, type of database, and expected output</li>\n",
    "</ul>\n",
    "</blockquote>"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Extracting Data Sources"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "<blockquote>The first data source we used was from Kaggle. We used the <a href=\"https://www.kaggle.com/mylesoneill/world-university-rankings\">World University Rankings</a> dataset. Its comprised of three separate ranking sources that attempt to rank institutions of higher education from best to worst. One list is from the Tiimes Higher Education World University Ranking, the other from Academic Ranking of World Universities (aka Shanghai Ranking), and the third is from the Center for World University Rankings. The second data source comprises <a href=\"https://www.kaggle.com/jessemostipak/college-tuition-diversity-and-pay?select=tuition_cost.csv\">tuition</a> costs. All files are in comma-separated format.\n",
    "<br>\n",
    "<br>\n",
    "\n",
    "These 3 rankings use different criteria to rank universities. Therefore, there are not many columns of data that are the same but it will be interesting to see where a university ranks on one list compared to another. The tuition cost file provides more detail about the institutions such as whether or not they're 2 or 4 year, public, private or for-profit, and includes the state the school is located in which isn't available in the ranking files.\n",
    "<br>\n",
    "<br>\n",
    "\n",
    "We used Pandas within a Jupyter Notebook to handle all phases of ETL.\n",
    "</blockquote>\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Transformation"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "<blockquote>The only column of data present in all files is the name of the university. This is not ideal to have a name field as the primary key. We decided to only focus on schools in the U.S. Also, the files cover different ranking years. Years 2012-2015 are the only years present in all 3 ranking files. Additionally, the tuition cost file only covers the 2018-19 academic year. With that we filtered 2 of the ranking files on the year field and country field. The Shanghai Ranking file didn't include a country column but we also found a crosswalk file which simply listed university names and country. We were able to merge these two lists and then filter(.loc) only U.S. schools to create a final dataframe for the Shanghai ranking.\n",
    "<br>\n",
    "<br>\n",
    "Additionally, there were no duplicates in any of the files as each school was listed only once. Also, we didn't feel the need to remove any columns as the point of selecting the datasets was to see the different criteria used by the different rankings. At the point of analysis the decision can be made to remove any extraneous columns.\n",
    "</blockquote>\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Loading"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "<blockquote>We loaded all data into a sql database using pgAdmin. We have a total of 4 tables, 1 for each of the different rankings, and a table for the tuition costs. The user has the option to join data using the school name or simply to view data one ranking at a time.<blockquote>"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Challenges"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "<blockquote>As mentioned previously, it wasn't an ideal situation to have a name column as the primary key. Therefore, when joining the Shanghai ranking with the crosswalk file, we encountered non-matching school names, when indeed the school was the same. An example of this is one list would list University of California-Berkeley and the other would list University of California, Berkeley. We encountered several inconsistencies such as this. We asked the TA how we should handle these type of discrepancies, with respect to the time restraint on the project and our novice experience. The TA mentioned some solutions but none were easy fixes and we were finally advised to ignore the non-matching records.</blockquote>"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Next Steps"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "<blockquote>It would be interesting to see how certain schools rank on the different lists. Analyzing whether or not a prominent school is higher on one list and why they might be lower on another since these rankings source from different countries. We'd also want to determine if a higher ranking correlates to higher tuition. Since we have the data, determining if 2-year schools are ranked lower than 4-year or not and do the same with school type: public, private, non-profit, or for-profit.</blockquote>"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.7.6"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 4
}
