title := Advanced Messaging Queuing Protocol (AMQP) Connection Info Property Version 1.0
source := src
output := html
sources := $(wildcard $(source)/*.md)

objects := $(patsubst %.md,%.html,$(subst $(source),$(output),$(sources)))

all:	$(objects)

$(output)/%.html:	$(source)/%.md
	mkdir -p ${output}
	cp -r styles images ${output}/.
	pandoc -f gfm -t html $< -c styles/markdown-styles-v1.7.3.css --toc --toc-depth=5 -s -o $@ --metadata title='$(title)'

.PHONY : clean

clean:
	rm -rf $(output)
