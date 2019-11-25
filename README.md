# Workshop for PyDay BCN 2019

These are the slides and notebook for a workshop _The magic of PySpark_ for
[PyDay Barcelona 2019](https://pybcn.org/pyday-bcn-2019/). 

You can find the slides
[here](https://github.com/rberenguel/pyspark_workshop/raw/master/pyspark_workshop.pdf)
(some images might look slightly blurry). I recommend you check the version with
[presenter
notes](https://github.com/rberenguel/pyspark_workshop/raw/master/pyspark_workshop_with_notes.pdf).

---

This presentation is formatted in Markdown and prepared to be used with
[Deckset](https://www.decksetapp.com/). The drawings were done on an iPad Pro
using [Procreate](https://procreate.art). **Here only the final PDF and the
source Markdown are available**. Sadly the animated gifs are just static images
in the PDF.

---

You can run the notebook in Binder

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/rberenguel/pyspark_workshop/master?filepath=pyspark_workshop.ipynb)

_Note_: The Arrow optimisation does not work in Binder. I'll try to fix it, but
it won't be ready for the workshop. Check the output notebook to see the impact
of these.

Or just read it here in Github by clicking
[here](https://github.com/rberenguel/pyspark_workshop/blob/master/pyspark_workshop.ipynb)
(no outputs) or
[here](https://github.com/rberenguel/pyspark_workshop/blob/master/pyspark_workshop_outputs.ipynb)
(with outputs)

---

## Thanks

- Thanks [FiveThirtyEight](https://fivethirtyeight.com) for making their
  datasets [available](https://github.com/fivethirtyeight/data/).
- The Binder start scripts are based on [Hyukjin Kwon's for his Spark Summit
  Europe 2019 talk](https://github.com/HyukjinKwon/spark-notebooks)
- Some of the images of the slides and explanations come from previous talks,
  [Internals of Speeding Up Pyspark with
  Arrow](https://github.com/rberenguel/pyspark-arrow-pandas) (Spark Summit
  Europe 2019) and [Welcome to Apache
  Spark](https://github.com/rberenguel/WelcomeToApacheSpark) (SoCraTesUK 2018
  with [Carlos Peña](http://twitter.com/crafty_coder))
- [PyBCN](https://pybcn.org) for the event and
  [Affectv](https://engineering.affectv.com) for supporting it

---

## Details on running the notebook

To take full advantage of the workshop without using Binder (locally) you'll
need

- PySpark installed (anything more recent than 2.3 should be fine)
- Jupyter installed
- Pandas and Arrow installed
- All able to talk to each other
- One or more datasets

---

The TL;DR if you don't want to use Docker should just be:

```
pip install pyarrow pandas pyspark numpy jupyter
```

---

You can install `pyspark` using `pip install pyspark`, installing it in the same
environment you have Jupyter installed should make them talk to each other just
fine. You should also run `pip install pyarrow`, although if this one fails for
some reason it's not a big problem. To make analysis more entertaining, also run
`pip install pandas`, again, all in the same environment. You can also run these
in conda, with `conda install -c conda-forge pyspark` although it might be more
convenient to use `pip` (`pyspark` can get easily confused with many python
environments)

---

If you are familiar enough with Docker, I recommend using a Docker container
instead.

Run this before the workshop:

```
docker pull rberenguel/pyspark_workshop
```

During the workshop (or before) you can use this docker container with

```
docker run --name pyspark_workshop -d -p 8888:8888 -p 4040:4040 -p 4041:4041 -v "$PWD":/home/jovyan rberenguel/pyspark_workshop
```

in the folder you want to create your Jupyter notebook. To open it in your
browser,

```
docker logs pyspark_workshop 
```

and open the URL provided in the logs (should look like
`http://127.0.0.1:8888/?token=36a20c93f0ee8cab4699e2460261e3b16787a68fbb034aee`)

This container installs Arrow on top of the usual `jupyter/pyspark`, to allow
for some additional optimisations in Spark.
