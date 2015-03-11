# ISN-Project

def drawmap(canvas, mapstruct):

    def square(x, y, fill):
        return canvas.create_rectangle((x+0)*size+margin, (y+0)*size+margin,
        (x+1)*size+margin, (y+1)*size+margin,
        width=0, fill=fill)

    def circle(x, y, fill):
        return canvas.create_oval((x+0.2)*size+margin, (y+0.2)*size+margin,(x+0.8)*size+margin, (y+0.8)*size+margin,width=0, fill=fill)
        switch = {'s': square,'c': circle}

    def setter(dic, kind, fill):
        def set(pos):
            x, y = pos
            dic[x, y] = switch[kind](x, y, fill)
            return set
            idstruct = {}, {}, {}, {}
            kinds = 'sscc'
            colors = WALL, EMPTY, BOX, PLAYER
            for dic, kind, fill, data in zip(idstruct, kinds, colors, mapstruct):
                map(setter(dic, kind, fill), data)
                return idstruct
