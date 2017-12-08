#Learn.co Educational Content License

Copyright (c) 2015 Flatiron School, Inc

The Flatiron School, Inc. owns this Educational Content. However, the Flatiron School supports the development and availability of educational materials in the public domain. Therefore, the Flatiron School grants Users of the Flatiron Educational Content set forth in this repository certain rights to reuse, build upon and share such Educational Content subject to the terms of the Educational Content License set forth [here](http://learn.co/content-license) (http://learn.co/content-license). You must read carefully the terms and conditions contained in the Educational Content License as such terms govern access to and use of the Educational Content.

Flatiron School is willing to allow you access to and use of the Educational Content only on the condition that you accept all of the terms and conditions contained in the Educational Content License set forth [here](http://learn.co/content-license) (http://learn.co/content-license).  By accessing and/or using the Educational Content, you are agreeing to all of the terms and conditions contained in the Educational Content License.  If you do not agree to any or all of the terms of the Educational Content License, you are prohibited from accessing, reviewing or using in any way the Educational Content.


attr_accessor :name, :artist_name
@@all = []

def self.create
  song = self.new
  self.all << song
  song
end

def self.new_by_name(string)
  song = self.new
  song.name = string
  song
end

def self.create_by_name(string)
  song = self.create
  song.name = string
  song
end

def self.find_by_name(string)
  self.all.find {|song|song.name == string
  }
end

def self.find_or_create_by_name(string)
  self.find_by_name(string) == nil ? self.create_by_name(string) : self.find_by_name(string)
end

def self.alphabetical
  self.all.sort_by {|song| song.name}
end

def self.new_from_filename(filename)
  info= filename.split(" - ")
    artist = info[0]
    song_name = info[1].split(".mp3").join

    song = self.new
    song.artist_name = artist
    song.name = song_name
    song
end

def self.create_from_filename(filename)
  info= filename.split(" - ")
    artist = info[0]
    song_name = info[1].split(".mp3").join

    song = self.create
    song.artist_name = artist
    song.name = song_name
    song

end

def self.destroy_all
  self.all.clear
end

def self.all
  @@all
end

def save
  self.class.all << self
end
