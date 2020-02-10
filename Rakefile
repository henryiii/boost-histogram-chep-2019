
NAME = 'boost_histogram'
EXTS = %w(.tex .bbl .bib)
PDFLATEX = 'pdflatex'
EXTRAS = %w(webofc.cls)

task default: [:dist, :build]

task dist: %W(#{NAME}.tar.gz)

file "#{NAME}.tar.gz" => EXTS.map{ |s| "#{NAME}#{s}" } + EXTRAS do |t|
  sh "tar -czf #{t.name} #{t.prerequisites.join(' ')}"
end

task build: %W(#{NAME}.pdf)

file "#{NAME}.pdf" => %W(#{NAME}.tex) do
  sh "#{PDFLATEX} #{NAME}.tex"
  sh "bibtex #{NAME}"
  sh "#{PDFLATEX} #{NAME}.tex"
end
