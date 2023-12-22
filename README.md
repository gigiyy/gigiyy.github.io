# Guixin's site

## prerequisite

install ruby; follow [jekyll](https://jekyllrb.com/docs/installation/macos/) insturctions till the installation of jekyll itself
```bash
brew install chruby ruby-install xz
ruby-install ruby 3.1.3
```

add below lines to your `.bash_profile`
```bash
source /opt/homebrew/opt/chruby/share/chruby/chruby.sh
source /opt/homebrew/opt/chruby/share/chruby/auto.sh
```

add `.ruby-version` file of with ruby version to your jekyll site project.
```text
3.1.3
```

## install jekyll and test locally

follow [this](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll) to install jekyll

if you want to do a update, like using new jekyll, ruby or bundle version, you can remove the `Gemfile.lock` first then do below:

```bash
bundle install
bundle exec jekyll serve
```

now you can push the code to github and let it do the job.
