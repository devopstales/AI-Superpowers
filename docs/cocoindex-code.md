
```bash
## Linux
uv tool install --upgrade cocoindex-code --prerelease explicit --with "cocoindex>=1.0.0a24"

## OSX
uv tool install --upgrade --prerelease=allow --python 3.12 \
--with "torch>=2.4.0" \
--with "sentence-transformers<=5.0.0" \
--with "numpy<2" \
 cocoindex-code

unset MAXOSX_DEPLOYMENT_TARGET

pkill -f ccc || true
ccc doctor
ccc index

## Skill
npx skills add cocoindex-io/cocoindex-code
```

```yaml
nano .cocoindex_code/settings.yml
embedding:
  provider: sentence-transformers
  model: sentence-transformers/all-MiniLM-L6-v2
  device: cpu
```