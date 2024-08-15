# GPP,NPP,RH转nc
这里是使用bin2cdf把GPP,NPP,RH数据从bin二进制格式转为nc格式
```bash
bin2cdf -h
#    bin2cdf (Jul 16 2024) Help
#    ==========================
# 
# Convert binary output into NetCDF files for LPJmL version 5.7.9
# 
# Usage: bin2cdf [-h] [-clm] [-floatgrid] [-firstyear y] [-nbands n] [-nstep n] [-cellsize size] [-swap]
#    [-global] [-short] [-compress level] [-units u] [-descr d] [-metafile] [-map name] varname gridfile
#    binfile netcdffile
# 
# Arguments:
# -h           print this help text
# -clm         file is in CLM format, default is raw
# -floatgrid   set data type of grid file to float, default is short
# -cellsize s  set cell size, default is 0.5 默认分辨率0.5
# -compress l  set compression level for NetCDF4 files
# -descr d     set long name in NetCDF file
# -units u     set units in NetCDF file 数据单位
# -global      use global grid for NetCDF file
# -swap        change byte order in binary file
# -short       data type of NetCDF data is short, default is float 
# -nbands n    number of bands, default is 1 波段默认是1
# -nstep n     number of steps per year, default is 1 一年步长数
# -ispft       output is PFT-specific 
# -firstyear f first year, default is 1901 数据第一年，默认是1901
# -metafile    set the input format to JSON metafile instead of raw
# -map name    name of map in JSON metafile, default is "band_names"
# varname      variable name in NetCDF file 变量名
# gridfile     filename of grid data file 网格文件
# binfile      filename of binary data file 二进制文件
# netcdffile   filename of NetCDF file created netcdf文件
```

## 输出数据GPP bin转netcdf
GPP(Gross Primary Productivity)单位是gC/m2/month 
```bash
bin2cdf -units gC/m2/month -descr "Gross Primary Productivity" -firstyear 1960 -nstep 12 gpp ./output/grid.bin ./output/mgpp.bin ./output/mgpp_res05_monthly_1960-2023.nc
```

## 输出数据NPP bin转netcdf
NPP(Net Primary Productivity)单位也是gC/m2/month
```bash
bin2cdf -units gC/m2/month -descr "Net Primary Productivity" -firstyear 1960 -nstep 12 npp ./output/grid.bin ./output/mnpp.bin ./output/mnpp_res05_monthly_1960-2023.nc
```

## 输出数据RH bin转netcdf
NPP(Heterotrophic Respiration)单位也是gC/m2/month
```bash
bin2cdf -units gC/m2/month -descr "Heterotrophic Respiration" -firstyear 1960 -nstep 12 rh ./output/grid.bin ./output/mrh.bin ./output/mrh_res05_monthly_1960-2023.nc
```
